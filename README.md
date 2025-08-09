# Simah Credit Scorer

A comprehensive credit scoring application that analyzes credit reports using AI-powered calculations. The system extracts data from PDF credit reports and applies sophisticated scoring algorithms to provide detailed credit analysis.

## 🚀 Features

- **PDF Credit Report Analysis**: Upload and extract data from credit report PDFs
- **AI-Powered Scoring**: Uses Claude Sonnet 3.5 for intelligent credit score calculations
- **Sectioned Scoring**: Breaks down credit scores into multiple categories (Traditional Score, Income & Employment, Alternative Data, Demographics, Vehicle Factors)
- **Interactive Configuration**: Web-based interface to configure scoring formulas and variables
- **Real-time Results**: Instant credit score analysis with detailed breakdowns
- **Modern UI**: Beautiful, responsive interface built with React

## 🏗️ Architecture

The application consists of two main components:

- **Backend**: FastAPI-based REST API with AI-powered calculation engine
- **Frontend**: React-based web interface for file upload and results display

## 🛠️ Prerequisites

- Docker and Docker Compose (for containerized setup)
- Node.js 16+ (for local frontend setup)
- Anthropic API key for AI calculations

## 📋 Setup Instructions

### Option 1: Docker Compose (Recommended)

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd simah_credit_scorer
   ```

2. **Create environment file**
   ```bash
   cd backend
   # Create .env file in the root directory
   echo "ANTHROPIC_API_KEY=your_anthropic_api_key_here" > .env
   ```

3. **Run with Docker Compose**
   ```bash
   docker-compose up --build
   ```

4. **Access the application**
   - Frontend: http://localhost:3000
   - Backend API: http://localhost:8000

### Option 2: Frontend Local Development

1. **Navigate to frontend directory**
   ```bash
   cd frontend
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start the development server**
   ```bash
   npm start
   ```

4. **Access the application**
   - Frontend: http://localhost:3000
   - Backend API: http://localhost:8000

## 🔧 Backend Structure

### Core Components

```
backend/
├── main.py                 # FastAPI application entry point
├── requirements.txt        # Python dependencies
├── api/
│   └── routes.py          # Main API routes (upload, extraction)
├── calculations/
│   ├── routes.py          # Calculation endpoints and LLM integration
│   └── config_handler.py  # Configuration management
├── extraction/
│   └── extractor.py       # PDF data extraction logic
├── data/
│   ├── calculations.json  # Scoring formulas and configurations
│   └── variables.json     # Variable definitions
└── extracted_tables_enhanced/
    └── all_tables.txt     # Extracted data storage
```

### Key Endpoints

- `POST /api/upload` - Upload and analyze credit report PDFs
- `GET /api/calculations/formula` - Get current scoring configuration
- `PUT /api/calculations/formula` - Update scoring configuration
- `GET /api/calculations/variables` - Get available variables
- `PUT /api/calculations/variables` - Update variables

### Main Functions

- **PDF Extraction**: Extracts structured data from credit report PDFs using PyMuPDF and Camelot
- **AI Calculation**: Uses Claude Sonnet 3.5 for intelligent credit scoring with structured output
- **Formula Engine**: Processes mathematical formulas with variable substitution and conditional logic
- **Configuration Management**: Handles scoring formulas and variable definitions with JSON storage

### Scoring System

The application uses a multi-section scoring approach:

1. **Traditional Score (35% weight)**
   - SIMAH Score calculation
   - Credit History analysis
   - Payment History evaluation

2. **Income & Employment (30% weight)**
   - Income Level assessment
   - Employment Stability
   - Employer Type classification
   - DTI Ratio calculation

3. **Alternative Data (20% weight)**
   - Bank Account Age
   - Average Monthly Balance
   - Regular Salary Deposits
   - Savings Ratio
   - Overdrafts analysis

4. **Demographics (15% weight)**
   - Age Factor
   - Marital and Dependents
   - Geographical Stability

## 🎨 Frontend Structure

### Core Components

```
frontend/
├── public/
│   ├── index.html         # Main HTML template
│   └── markaba-logo.png   # Application logo
├── src/
│   ├── App.js             # Main React application with routing
│   ├── index.js           # React entry point
│   ├── App.css            # Global styles
│   └── pages/
│       ├── Upload.js      # File upload interface with drag-and-drop
│       ├── Upload.css     # Upload page styles
│       ├── Results.js     # Results display with scoring breakdown
│       ├── Results.css    # Results page styles
│       ├── Configure.js   # Formula configuration interface
│       └── Configure.css  # Configure page styles
└── package.json           # Node.js dependencies and scripts
```

### Key Features

- **Upload Page**: Drag-and-drop PDF upload with validation and progress indicators
- **Results Page**: Interactive credit score display with section breakdowns and visual charts
- **Configure Page**: Formula editor with variable selection, testing, and real-time validation
- **Responsive Design**: Mobile-friendly interface with modern styling and animations

### Component Architecture

- **Upload Component**: Handles file selection, validation, and upload process with error handling
- **Results Component**: Displays credit scores with visual charts, section breakdowns, and detailed formula results
- **Configure Component**: Manages scoring formulas and variable configurations with drag-and-drop functionality
- **Navigation**: Seamless routing between different application sections with React Router

## 🔑 Environment Variables

### Required

- `ANTHROPIC_API_KEY`: Your Anthropic API key for AI-powered calculations

### Optional

- `UVICORN_WORKERS`: Number of Uvicorn workers (default: 1)

## 📊 Usage

1. **Upload Credit Report**: Navigate to the upload page and select a PDF credit report
2. **View Results**: After processing, view the detailed credit score breakdown with section analysis
3. **Configure Scoring**: Use the configure page to customize scoring formulas and variables
4. **Analyze Data**: Review section-by-section scoring with formula details and variable usage

## 🚀 Deployment

### Production Deployment

1. **Build the application**
   ```bash
   # Frontend
   cd frontend
   npm run build
   
   # Backend
   cd backend
   pip install -r requirements.txt
   ```

2. **Set up environment variables**
   ```bash
   export ANTHROPIC_API_KEY=your_production_key
   ```

3. **Run with production settings**
   ```bash
   # Backend
   uvicorn main:app --host 0.0.0.0 --port 8000 --workers 4
   
   # Frontend (serve build directory)
   npx serve -s build -l 3000
   ```


## 🆘 Documentation

- Review the API endpoints at `http://localhost:8000/docs`

