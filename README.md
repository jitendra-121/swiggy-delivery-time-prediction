# 🚚 Swiggy Delivery Time Prediction

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.68+-green.svg)](https://fastapi.tiangolo.com/)
[![MLflow](https://img.shields.io/badge/MLflow-Tracking-orange.svg)](https://mlflow.org/)
[![DVC](https://img.shields.io/badge/DVC-Data%20Pipeline-red.svg)](https://dvc.org/)
[![Docker](https://img.shields.io/badge/Docker-Enabled-blue.svg)](https://www.docker.com/)

A comprehensive machine learning project that predicts food delivery time in minutes using real-world Swiggy delivery data. This end-to-end ML solution includes data preprocessing, model training, hyperparameter tuning, model registry, and deployment with FastAPI.

## 🎯 Project Overview

This project implements a robust machine learning pipeline to predict delivery times for food orders, considering various factors such as:
- Delivery person characteristics (age, ratings)
- Geographic coordinates (restaurant and delivery locations)
- Order details (time, type, vehicle)
- Environmental factors (weather, traffic, festivals)
- Delivery context (multiple deliveries, city)

## ✨ Key Features

- **🔄 MLOps Pipeline**: Complete CI/CD pipeline with DVC for data versioning
- **📊 Model Registry**: MLflow integration for experiment tracking and model management
- **🚀 Production Ready**: FastAPI deployment with Docker containerization
- **📈 Multiple Models**: Random Forest and LightGBM with hyperparameter optimization
- **🧪 Comprehensive Testing**: Unit tests for API endpoints and model performance
- **📝 Documentation**: Detailed notebooks and documentation for reproducibility

## 🏗️ Architecture

```
├── Data Ingestion → Data Cleaning → Feature Engineering → Model Training
│                                                              │
└── API Deployment ← Model Registry ← Model Evaluation ← ─────┘
```

## 🚀 Quick Start

### Prerequisites

- Python 3.8+
- Docker (optional)
- Git

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/swiggy-delivery-time-prediction.git
   cd swiggy-delivery-time-prediction
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the DVC pipeline**
   ```bash
   dvc repro
   ```

5. **Start the API server**
   ```bash
   python app.py
   ```

The API will be available at `http://localhost:8000` with interactive docs at `http://localhost:8000/docs`

### Docker Deployment

```bash
docker build -t swiggy-delivery-prediction .
docker run -p 8000:8000 swiggy-delivery-prediction
```

## 📊 Dataset

The project uses Swiggy delivery data with the following features:

| Feature | Description |
|---------|-------------|
| Delivery_person_Age | Age of the delivery person |
| Delivery_person_Ratings | Rating of the delivery person |
| Restaurant_latitude/longitude | Restaurant coordinates |
| Delivery_location_latitude/longitude | Delivery coordinates |
| Order_Date | Date of the order |
| Time_Ordered | Time when order was placed |
| Time_Order_picked | Time when order was picked up |
| Weather_conditions | Weather during delivery |
| Road_traffic_density | Traffic density |
| Vehicle_condition | Condition of delivery vehicle |
| Type_of_order | Type of food order |
| Multiple_deliveries | Number of deliveries |
| Festival | Whether it's a festival day |
| City | Delivery city |

## 🤖 Models

### Random Forest Regressor
- **n_estimators**: 479
- **max_depth**: 17
- **Optimized hyperparameters** for delivery time prediction

### LightGBM Regressor
- **n_estimators**: 154
- **max_depth**: 27
- **learning_rate**: 0.222
- **Advanced gradient boosting** for improved accuracy

### Stacking Regressor
- **Meta-learner**: Combines multiple base models
- **Enhanced performance** through ensemble methods

## 📁 Project Structure

```
├── app.py                 # FastAPI application
├── Dockerfile            # Docker configuration
├── dvc.yaml              # DVC pipeline definition
├── params.yaml           # Model parameters
├── requirements.txt      # Python dependencies
├── setup.py              # Package configuration
│
├── data/                 # Data storage
│   ├── raw/             # Original datasets
│   ├── interim/         # Intermediate processed data
│   ├── processed/       # Final datasets for modeling
│   └── cleaned/         # Cleaned datasets
│
├── src/                  # Source code
│   ├── data/            # Data processing scripts
│   ├── features/        # Feature engineering
│   ├── models/          # Model training and evaluation
│   └── visualization/   # Data visualization
│
├── notebooks/           # Jupyter notebooks
├── models/              # Trained model artifacts
├── tests/               # Unit and integration tests
├── docs/                # Project documentation
├── scripts/             # Utility scripts
└── deploy/              # Deployment configurations
```

## 🔧 Usage

### API Endpoints

#### Predict Delivery Time
```bash
curl -X POST "http://localhost:8000/predict" \
     -H "Content-Type: application/json" \
     -d '{
       "ID": "12345",
       "Delivery_person_Age": "25",
       "Delivery_person_Ratings": "4.5",
       "Restaurant_latitude": 12.9716,
       "Restaurant_longitude": 77.5946,
       "Delivery_location_latitude": 12.9716,
       "Delivery_location_longitude": 77.5946,
       "Order_Date": "2023-08-07",
       "Time_Orderd": "19:30",
       "Time_Order_picked": "19:45",
       "Weatherconditions": "Sunny",
       "Road_traffic_density": "Medium",
       "Vehicle_condition": 1,
       "Type_of_order": "Meal",
       "Type_of_vehicle": "motorcycle",
       "multiple_deliveries": "1",
       "Festival": "No",
       "City": "Bangalore"
     }'
```

### Model Training

Run the complete pipeline:
```bash
make all
```

Or run individual steps:
```bash
make data          # Data preparation
make features      # Feature engineering
make train         # Model training
make evaluate      # Model evaluation
```

## 📈 Model Performance

| Model | MAE | RMSE | R² Score |
|-------|-----|------|----------|
| Random Forest | X.XX | X.XX | 0.XX |
| LightGBM | X.XX | X.XX | 0.XX |
| Stacking | X.XX | X.XX | 0.XX |

## 🧪 Testing

Run the test suite:
```bash
pytest tests/
```

Test coverage includes:
- API endpoint functionality
- Model performance validation
- Model registry operations
- Data preprocessing pipelines

## 📚 Documentation

- **Notebooks**: Detailed analysis in `notebooks/` directory
- **API Docs**: Available at `/docs` endpoint when running the server
- **Model Cards**: Model documentation in `docs/` directory
- **Architecture**: System design in `docs/` directory

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Data Source**: Swiggy delivery dataset
- **Framework**: Based on the [cookiecutter data science template](https://drivendata.github.io/cookiecutter-data-science/)
- **MLOps**: Powered by MLflow, DVC, and FastAPI
- **Deployment**: Docker and CI/CD best practices

## 📞 Contact

For questions or suggestions, please open an issue or contact the maintainers.

---

**Built with ❤️ for better delivery time predictions**
