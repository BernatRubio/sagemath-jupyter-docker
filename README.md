# SageMath Jupyter Notebook in Docker

Easily run **SageMath** with Jupyter Notebook using **Docker** and **Docker Compose**.

## 🚀 Features
- **Zero local installation:**  Run SageMath without installing it on your host.
- **Jupyter Notebook Interface:** Start working immediately with Jupyter’s interactive interface.
- **Persistent Storage:** All your notebooks are stored in the notebooks/ directory.
- **Local Access:** The service binds to 127.0.0.1, ensuring it’s only accessible from your machine (by default).
- **Customizable Security:** Token authentication is disabled by default for ease of use but can be enabled for public or shared environments.

## 📥 About the Docker Image
This setup uses the official **SageMath Docker image**, maintained by the SageMath team.  
📌 **Docker Hub:** [sagemath/sagemath](https://hub.docker.com/r/sagemath/sagemath/)  
📌 **GitHub Repository:** [SageMath Docker Images](https://github.com/sagemath/docker-images)  

This ensures you are using the latest, maintained version of SageMath in a containerized environment.

## 📦 Installation

### **1️⃣ Install Docker & Docker Compose**
Ensure you have **Docker** and **Docker Compose** installed.

- **Linux/macOS:**  
  ```sh
  curl -fsSL https://get.docker.com | sh
  sudo systemctl start docker
  sudo systemctl enable docker
  ```
- **Windows:** [Download Docker](https://www.docker.com/products/docker-desktop/)

### **2️⃣ Clone the Repository**
```sh
git clone https://github.com/BernatRubio/sagemath-jupyter-docker.git
cd sagemath-jupyter-docker
```

### **3️⃣ Start SageMath Jupyter**
```sh
docker compose up -d
```

### **4️⃣ Open Jupyter Notebook**
Visit **[http://127.0.0.1:8888](http://127.0.0.1:8888)** in your browser.

## 📂 File Structure
```
sagemath-jupyter-docker/
│── notebooks/      # All Jupyter notebooks will be stored here
│── compose.yaml    # Docker Compose file to start SageMath
│── README.md       # Documentation
```

## 🛑 Stopping the Container
```sh
docker compose down
```

## 🛠 Customization

### **Enable Authentication (Recommended for Public Networks)**
By default, this setup **disables token authentication** for easier access. If you want to enable authentication, modify the `compose.yaml` file:

```yaml
command: >
  sage -n jupyter --no-browser --ip=0.0.0.0 --port=8888
```

## 🐳 Running Without Docker Compose
If you prefer using `docker run`, you can start the container with:

```sh
docker run -p 127.0.0.1:8888:8888 -v $(pwd)/notebooks:/home/sage/notebooks sagemath/sagemath sage -n jupyterlab --no-browser --ip=0.0.0.0 --port=8888 --NotebookApp.token='' --NotebookApp.password='' --NotebookApp.notebook_dir='/home/sage/notebooks'
```

## 🎯 Contributions & Issues
Feel free to contribute or report any issues! Fork the repo, make improvements, and submit a **pull request**.

## 📜 License
This project is open-source and available under the **MIT License**.
See the [LICENSE](LICENSE) file for details.
