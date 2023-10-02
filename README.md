Welcome to your new dbt project!

### Using the starter project

Try running the following commands:
- dbt run
- dbt test


### Resources:
- Learn more about dbt [in the docs](https://docs.getdbt.com/docs/introduction)
- Check out [Discourse](https://discourse.getdbt.com/) for commonly asked questions and answers
- Join the [dbt community](http://community.getbdt.com/) to learn from other analytics engineers
- Find [dbt events](https://events.getdbt.com) near you
- Check out [the blog](https://blog.getdbt.com/) for the latest news on dbt's development and best practices


### Loading CSV file:
In dbt (data build tool), seeding is a process that allows you to load static data into your data warehouse. This can be very helpful for loading reference data, like a list of countries or states, or parameters that are used in your transformations.

When working with dbt Cloud integrated with GitHub and BigQuery, there are several steps to follow to work through the query and add a CSV to your dbt project:

1. **Prepare the CSV File**:
    - Make sure your CSV file is properly formatted and contains the data you want to seed into your BigQuery database.

2. **Upload the CSV to your GitHub Repository**:
    - In your dbt project repository on GitHub, create a directory named `seeds/` (if it doesn’t already exist).
    - Upload your CSV file to the `seeds/` directory.

3. **Update dbt Configuration**:
    - In your `dbt_project.yml` file, ensure that the `seeds` directory is specified. It should look something like this:
    ```yaml
    seeds:
      your_project_name:
        +schema: your_schema_name
    ```
    - This is to ensure dbt knows where to find the seed data and where to load it in BigQuery.

4. **Pull the Changes in dbt Cloud**:
    - Once the CSV file is in your GitHub repository and your dbt configuration is updated, go to dbt Cloud.
    - You may need to trigger a pull to fetch the latest changes from your GitHub repository.

5. **Run dbt Seed**:
    - In dbt Cloud, navigate to the project and the relevant environment.
    - Run the `dbt seed` command either through the dbt Cloud UI or by configuring a job to run `dbt seed`.
    - This will load your CSV data into the specified schema in BigQuery.

6. **Verify**:
    - After the seeding process is complete, verify that the data has been loaded correctly in BigQuery.

7. **Continue with your dbt Work**:
    - Now that your seed data is loaded into BigQuery, you can reference it in your dbt models and continue with your dbt work.

By following these steps, you should be able to get your static CSV data loaded into BigQuery using dbt Cloud, GitHub, and the `dbt seed` command.
