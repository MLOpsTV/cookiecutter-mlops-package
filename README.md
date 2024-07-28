# MLOps Package Cookiecutter

[![Release](https://img.shields.io/github/v/release/fmind/cookiecutter-mlops-package)](https://github.com/fmind/cookiecutter-mlops-package/releases)
[![License](https://img.shields.io/github/license/fmind/cookiecutter-mlops-package)](https://github.com/fmind/cookiecutter-mlops-package/blob/main/LICENSE.txt)

**Jumpstart your MLOps projects with this comprehensive Cookiecutter template**.

The template provides a robust foundation for building, testing, packaging, and deploying Python packages and Docker Images tailored for MLOps.

You can also leverage the **[MLOps Coding Course](https://mlops-coding-course.fmind.dev/)** to learn about MLOps best practices, and check the **[MLOps Python Package](https://github.com/fmind/mlops-python-package)** for getting started with Predictive ML projects.

## Philosophy

This [Cookiecutter](https://cookiecutter.readthedocs.io/) is designed to be a common ground for diverse MLOps environments. Whether you're working with [Kubernetes](https://www.kubeflow.org/), [Vertex AI](https://cloud.google.com/vertex-ai), [Databricks](https://www.databricks.com/), [Azure ML](https://azure.microsoft.com/en-us/products/machine-learning), or [AWS SageMaker](https://aws.amazon.com/sagemaker/), the core principles of using Python packages and Docker images remain consistent.

This template equips you with the essentials for creating, testing, and packaging your code, providing a solid base for integration into your chosen platform. To fully leverage its capabilities within a specific environment, you might need to combine it with external tools like [Airflow](https://airflow.apache.org/) for orchestration or platform-specific SDKs for deployment.

You have the freedom to structure your `src/` and `tests/` directories according to your preferences. Alternatively, you can draw inspiration from the structure used in the [MLOps Python Package](https://github.com/fmind/mlops-python-package) project for a ready-made organization.

## Key Features

* **Streamlined Project Structure:** A well-defined directory layout for source code, tests, documentation, tasks, and Docker configurations.
* **Poetry Integration:** Effortless dependency management and packaging with Poetry.
* **Automated Testing and Checks:** Pre-configured workflows using Pytest, Ruff, Mypy, Bandit, and Coverage to ensure code quality, style, security, and type safety.
* **Pre-commit Hooks:** Automatic code formatting and linting with Ruff and other pre-commit hooks to maintain consistency.
* **MLflow Project Ready:** An MLproject file for executing jobs using MLflow, allowing for easy experimentation and tracking.
* **Dockerized Deployment:** Dockerfile and docker-compose.yml for building and running the package within a containerized environment.
* **Invoke Task Automation:** PyInvoke tasks to simplify development workflows such as cleaning, installing, formatting, checking, building, documenting, and running MLflow projects.
* **Comprehensive Documentation:**  pdoc generates API documentation, and Markdown files provide clear usage instructions.
* **GitHub Workflow Integration:** Continuous integration and deployment workflows are set up using GitHub Actions, automating testing, checks, and publishing.

## Quick Start

1. **Generate your project:**

```bash
pip install cookiecutter
cookiecutter gh:fmind/cookiecutter-mlops-package
```

You'll be prompted for the following variables:

- `user`: Your GitHub username.
- `name`: The name of your project.
- `repository`: The name of your GitHub repository.
- `package`: The name of your Python package.
- `license`: The license for your project.
- `version`: The initial version of your project.
- `description`: A brief description of your project.
- `python_version`: The Python version to use (e.g., 3.12).
- `mlflow_version`: The MLflow version to use (e.g., 2.14.3).

2. **Initialize a git repository:**

```bash
cd {{ cookiecutter.repository }}
git init
```

3. **Enable GitHub Pages Workflow:**

- Navigate to your repository settings on GitHub: "Settings" -> "Actions" -> "General."
- Under "Workflow permissions," ensure "Read and write permissions" is selected.
    - This allows the workflow to automatically publish your documentation.

4. **Explore the generated project:**

- `src/{{cookiecutter.package}}`: Your Python package source code.
- `tests/`: Unit tests for your package.
- `tasks/`: PyInvoke tasks for automation.
- `Dockerfile`: Configuration for building your Docker image.
- `docker-compose.yml`: Orchestration file for running MLflow and your project.
- `MLproject`: MLflow project definition.

5. **Start developing!**

Use the provided Invoke tasks to manage your development workflow:

- `invoke installs`: Install dependencies and pre-commit hooks.
- `invoke formats`: Format your code.
- `invoke checks`: Run code quality, type, security, and test checks.
- `invoke docs`: Generate API documentation.
- `invoke packages`: Build your Python package.
- `invoke projects`: Run MLflow projects.
- `invoke containers`: Build and run your Docker image.

## Example Usage

### Running an MLflow Project

After installing dependencies and setting up MLflow:

```bash
invoke projects
```

This will execute the "main" job defined in your `MLproject` file. You can specify different jobs using the `-P job=your_job_name` flag.

### Building and Running Your Docker Image

```bash
invoke containers
```

This builds a Docker image based on your `Dockerfile` and runs it. The `CMD` in the Dockerfile executes your package with the `--help` flag.

## Contributions

We welcome contributions to enhance this Cookiecutter template.

Feel free to open issues or pull requests for any improvements, bug fixes, or feature requests.

## License

This project is licensed under the MIT License. See the `LICENSE.txt` file for details.