# SHL Assessment Recommendation System

This repository contains a complete implementation of an intelligent recommendation system for SHL assessments, designed to help hiring managers find the right assessments for their job roles.

## Features

- **Natural Language Queries**: Enter job descriptions or specific requirements in natural language
- **Intelligent Matching**: Uses TF-IDF vectorization and semantic similarity to match queries with appropriate assessments
- **File Upload Support**: Upload text files or PDFs containing job descriptions
- **Evaluation Metrics**: View Recall@3 and MAP@3 metrics for recommendation quality
- **Full API Access**: Access the recommendation engine programmatically

## Quick Start

### Running Locally

1. Clone this repository:
   ```
   git clone https://github.com/yourusername/shl-assessment-recommender.git
   cd shl-assessment-recommender
   ```

2. Install dependencies:
   ```
   pip install -r streamlit_requirements.txt
   ```

3. Start the Streamlit application:
   ```
   streamlit run app.py
   ```

4. The application will be available at `http://localhost:8501`

5. For API access, start the FastAPI server in a separate terminal:
   ```
   uvicorn api:app --host 0.0.0.0 --port 8000
   ```

### Deployment

#### Streamlit Cloud Deployment

1. Fork this repository to your GitHub account
2. Go to [Streamlit Cloud](https://streamlit.io/cloud)
3. Sign in with your GitHub account
4. Click "New app"
5. Select your repository, branch, and app.py file
6. Advanced Settings:
   - Set Python requirements file to `streamlit_requirements.txt`
7. Click "Deploy"

#### Render Deployment

**For the Streamlit App:**
1. Sign up for [Render](https://render.com)
2. Create a new Web Service
3. Connect your GitHub repository
4. Configure the service:
   - Name: `shl-recommendation-frontend`
   - Environment: `Python 3`
   - Build Command: `pip install -r streamlit_requirements.txt`
   - Start Command: `streamlit run app.py`
   - Plan: Free

**For the API:**
1. Create another Web Service
2. Connect to the same repository
3. Configure the service:
   - Name: `shl-recommendation-api`
   - Environment: `Python 3`
   - Build Command: `pip install -r streamlit_requirements.txt`
   - Start Command: `uvicorn api:app --host 0.0.0.0 --port 10000`
   - Plan: Free

## Project Structure

```
shl-assessment-recommender/
├── app.py                    # Streamlit web application
├── api.py                    # FastAPI backend
├── data_processor.py         # Data loading and embedding
├── recommendation_engine.py  # Core recommendation logic
├── evaluation.py             # System evaluation metrics
├── data/                     # Contains assessment data
│   └── shl_assessments.json  # Assessment catalog
├── uploads/                  # Directory for uploaded files
├── .streamlit/               # Streamlit configuration
│   └── config.toml           # Server settings
├── streamlit_requirements.txt # Package dependencies for Streamlit deployment
├── deployment_requirements.txt # Detailed requirements for deployment
└── README.md                 # This file
```

## API Documentation

When running locally, API documentation is available at `http://localhost:8000/docs`

### Health Check Endpoint
```
GET /health
```

### Recommendation Endpoint
```
POST /recommend
{
    "query": "Your job description or query text",
    "url": "Optional URL to fetch additional content",
    "max_results": 10
}
```

### GET Recommendation Endpoint
```
GET /recommend?query=Your+job+description&max_results=10
```

## Implementation Details

### Data Processing
- Assessment data is stored in JSON format
- Text is processed using TF-IDF vectorization for semantic similarity
- No external API keys or services required

### Evaluation
- System performance is measured using Recall@3 and MAP@3 metrics
- Test cases are included in the evaluation module

## Troubleshooting

- **Missing Data**: Ensure the data directory exists and contains `shl_assessments.json`
- **File Upload Issues**: Check that the uploads directory exists and is writable
- **API Connection Errors**: Verify that both services are running correctly

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
