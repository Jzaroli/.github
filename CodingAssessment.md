<p align="center">
  <img src="./PreswaldBanner.png" alt="Logo">
</p>

# **Preswald Coding Assessment Guide**

## **Overview**

The goal is to contribute an example to the **`examples/`** folder of the **[Preswald GitHub repository](https://github.com/StructuredLabs/preswald)**. This should take **approximately 30 minutes** to complete.

## **Task Description**

Your task is to:

1. Find a dataset
2. Write a Preswald app 
3. Deploy your app
4. Submit a PR to the `examples/` folder.

## **Step-by-Step Instructions**

### **1. Set Up Your Environment**

Install Preswald. If you have any troubles, use a virtual env. [Guide](https://docs.preswald.com/usage/troubleshooting#set-up-a-virtual-environment)

pip install preswald

Create a new project directory:

preswald init my_example_project
cd my_example_project

---

### **2. Choose a Dataset**

Either use [Iris Dataset](https://gist.github.com/netj/8836201#file-iris-csv )

or

Select/download a dataset from any of these sources:

- [Kaggle Datasets](https://www.kaggle.com/datasets)
- [Data.gov](https://www.data.gov/)
- [Open Data Repositories](https://github.com/awesomedata/awesome-public-datasets)
- Any csv (e.g., weather, finance, sports stats)

Place your dataset in the `data/` folder of your project.

---

### **3. Implement Your Preswald App**

Modify `hello.py` to include the following:

1. **Load the dataset**
            
        from preswald import connect, get_df
        
        connect()  # Initialize connection to preswald.toml data sources
        df = get_df("my_dataset")  # Load data
        
2. **Query or manipulate the data**
            
        
        from preswald import query
        
        sql = "SELECT * FROM my_dataset WHERE value > 50"
        filtered_df = query(sql, "my_dataset")
        
3. **Build an interactive UI**
            
        from preswald import table, text
        
        text("# My Data Analysis App")
        table(filtered_df, title="Filtered Data")
        
    - Add user controls:
        ```
        from preswald import slider, view
        threshold = slider("Threshold", min_val=0, max_val=100, default=50)
        table(df[df["value"] > threshold], title="Dynamic Data View")
        ```
4. **Create a visualization**

    ```
    from preswald import plotly
    import plotly.express as px
    
    fig = px.scatter(df, x="column1", y="column2", color="category")
    plotly(fig)
    ```
---

### **4. Deploy Your App to Structured Cloud**

Once your app is running locally, deploy it.

1. **Get an API key**
    
    - Go to [app.preswald.com](https://app.preswald.com/)
    - Create a New Organization (top left corner)
    - Navigate to **Settings > API Keys**
    - Generate and copy your **Preswald API key**
      
2. **Deploy your app using the following command:**
    
    preswald deploy --target structured --github <your-github-username> --api-key <structured-api-key> hello.py

    Replace `<your-github-username>` and `<structured-api-key>` with your credentials.
    
3. **Verify the deployment**
    
    - Once deployment is complete, a **live preview link** will be provided.
    - Open the link in your browser and verify that your app is running.

---

### **5. Add Your Example to the Repository**

1. **Create a new folder** inside `examples/` in the Preswald GitHub repository.
    - Name it based on your dataset (e.g., `examples/my_dataset_example`).
2. **Include:**
    - **Your script** (`hello.py` or another filename).
    - **Your dataset** (if small) in the `data/` folder, or a link to it in `README.md`.
    - **A README.md file** explaining:
        - The dataset source.
        - What your app does.
        - How to run and deploy it.

**Example folder structure:**

examples/my_dataset_example/
├── hello.py
├── data/
│   ├── my_dataset.csv
├── README.md

---

### **6. Submit a Pull Request**

Once you've completed your work:

1. **Fork [Preswald](https://github.com/StructuredLabs/preswald)**.
2. **Add your example to `examples/`**.
3. **Push your changes to your fork**.
4. **Open a PR** with a brief description of your contribution. (See [guide](https://github.com/StructuredLabs/preswald/blob/main/CONTRIBUTING.md) if you need help).

---

## **Need Help?**

- Check the **[Preswald Documentation](https://docs.preswald.com/)**.
- Reach out via [**GitHub Issues**](https://github.com/StructuredLabs/preswald/issues).
- Email **[founders@structuredlabs.com](mailto:founders@structuredlabs.com)**.

---

### **After completing this, reach out to founders@structuredlabs.com with subject line - `<your name> Coding Assesment Completed`** with a link to your PR + Deployed link.
