 # 🚚 Multi-Agent Delivery Communication System

A sophisticated AI-powered system that bridges communication gaps between consumers and delivery agents using multiple specialized AI agents. This system provides real-time translation, intelligent auto-responses, voice memo management, and comprehensive delivery order tracking.

## ✨ Features

### 🤖 AI-Powered Agents

- **🌐 Translator Agent**: Multi-language translation with speech-to-text and text-to-speech capabilities
- **📅 Auto-Responder Agent**: Calendar-aware intelligent responses based on availability
- **🎤 Voice Memo Agent**: Create and manage voice instructions for delivery personnel
- **👨‍💼 Supervisor Agent**: Orchestrates all agents and monitors system health
- **📦 Delivery Order Agent**: Comprehensive delivery tracking and management

### 🎯 Core Capabilities

- **Seamless Translation**: Support for 12+ languages with Google Cloud APIs
- **Smart Auto-Responses**: Context-aware responses based on calendar status
- **Voice Processing**: High-quality speech synthesis and recognition
- **Real-time Monitoring**: Live system health and performance tracking
- **Multi-modal Communication**: Text, voice, and hybrid language support

## 🏗️ Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Frontend      │    │   Backend       │    │   Google APIs   │
│   (Next.js)     │◄──►│   (FastAPI)     │◄──►│   (Speech,      │
│                 │    │                 │    │    Translate,   │
│ • Translation   │    │ • Translator    │    │ • Auto Responder│
│ • Auto Response │    │ • Auto Responder│    │ • Voice Memo    │
│ • Voice Memo    │    │ • Voice Memo    │    │ • Monitoring    │
│ • Monitoring    │    │ • Supervisor    │    │                 │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

## 🛠️ Technology Stack

### Backend
- **Python 3.8+** with FastAPI framework
- **Agno** for AI agent orchestration
- **Google Cloud APIs**: Speech-to-Text, Translate, Text-to-Speech, Calendar
- **SQLite** database with comprehensive logging
- **Docker** containerization support

### Frontend
- **Next.js 14** with React 18
- **TypeScript** for type safety
- **Tailwind CSS** for modern styling
- **React Hook Form** for form management
- **Axios** for API communication

## 🚀 Quick Start

### Prerequisites

1. **Python 3.8+** (3.11+ recommended)
2. **Node.js 18+**
3. **Docker** (optional, but recommended)
4. **Google Cloud Project** with enabled APIs

### Option 1: Docker (Recommended)

```bash
# Clone and navigate to the project
cd app

# Start the entire system
docker-compose up -d

# Access the applications
# Frontend: http://localhost:3000
# Backend: http://localhost:8000
# API Docs: http://localhost:8000/docs
```

### Option 2: Manual Setup

#### Backend Setup

```bash
# Navigate to backend directory
cd app/backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
cp env.example .env
# Edit .env with your Google Cloud credentials

# Run the backend
python main.py
```

#### Frontend Setup

```bash
# Navigate to frontend directory
cd app/frontend

# Install dependencies
npm install

# Set up environment variables
cp env.example .env.local
# Edit .env.local with your API URL

# Start development server
npm run dev
```

## 🔑 Configuration

### Google Cloud Setup

1. **Create a Google Cloud Project**
2. **Enable required APIs**:
   ```bash
   gcloud services enable speech.googleapis.com
   gcloud services enable translate.googleapis.com
   gcloud services enable texttospeech.googleapis.com
   gcloud services enable calendar.googleapis.com
   ```
3. **Create a service account** and download the JSON key
4. **Set environment variables** in your `.env` file

### Environment Variables

**Backend** (`app/backend/.env`):
```env
GOOGLE_CLOUD_PROJECT=your-project-id
GOOGLE_CLOUD_LOCATION=us-central1
GOOGLE_APPLICATION_CREDENTIALS=path/to/service-account-key.json
DEFAULT_MODEL=gemini-1.5-flash
HOST=0.0.0.0
PORT=8000
```

**Frontend** (`app/frontend/.env.local`):
```env
NEXT_PUBLIC_API_URL=http://localhost:8000
```

## 📱 Usage

### Web Interface

1. **Open the frontend** at http://localhost:3000
2. **Navigate between tabs**:
   - **Translation**: Multi-language text translation
   - **Auto Response**: Generate calendar-aware responses
   - **Voice Memo**: Create voice instructions
   - **Enhanced Voice**: Real-time voice processing
   - **Monitoring**: System health and performance

### API Endpoints

#### Core Services
- `POST /translate` - Text translation
- `POST /auto-response` - Generate auto-responses
- `POST /voice-memo` - Create voice memos
- `GET /voice-memos/{user_id}` - Retrieve user memos

#### Monitoring
- `GET /agents/status` - Agent health status
- `POST /agents/monitor` - System health check
- `GET /report` - Generate system reports

#### Delivery Management
- `POST /delivery-order` - Process delivery requests
- `GET /order/{order_id}` - Get order details
- `PUT /order/{order_id}` - Update order preferences

### Example API Usage

```bash
# Translate text
curl -X POST "http://localhost:8000/translate" \
  -H "Content-Type: application/json" \
  -d '{"text": "Hello world", "target_lang": "Spanish"}'

# Generate auto-response
curl -X POST "http://localhost:8000/auto-response" \
  -H "Content-Type: application/json" \
  -d '{"status": "busy", "language": "Spanish"}'

# Check system health
curl "http://localhost:8000/agents/status"
```

## 🔧 Development

### Project Structure

```
app/
├── backend/                    # Backend application
│   ├── agents/                # AI agent implementations
│   │   ├── translator_agent.py
│   │   ├── auto_responder_agent.py
│   │   ├── voice_memo_agent.py
│   │   ├── supervisor_agent.py
│   │   └── delivery_order_agent.py
│   ├── database/              # Database management
│   ├── utils/                 # Utility functions
│   ├── main.py               # Main application entry point
│   ├── config.py             # Configuration settings
│   ├── models.py             # Data models
│   └── requirements.txt      # Python dependencies
├── frontend/                  # Frontend application
│   ├── app/                  # Next.js app directory
│   ├── components/           # React components
│   ├── lib/                  # Utility libraries
│   ├── package.json          # Node.js dependencies
│   └── next.config.js        # Next.js configuration
└── docker-compose.yml         # Docker orchestration
```

### Adding New Agents

1. **Create agent class** in `backend/agents/`
2. **Inherit from base patterns** and implement required methods
3. **Register with supervisor** in `main.py`
4. **Add frontend components** in `frontend/components/`
5. **Update API endpoints** as needed

### Testing

```bash
# Backend tests
cd app/backend
python -m pytest

# Frontend tests
cd app/frontend
npm test

# Integration tests
cd app
docker-compose -f docker-compose.test.yml up
```

## 📊 Monitoring & Analytics

The system provides comprehensive monitoring:

- **Real-time Agent Health**: Monitor all agent statuses
- **Performance Metrics**: Track response times and success rates
- **Error Detection**: Automatic failure detection and escalation
- **Usage Analytics**: Communication patterns and language preferences
- **System Reports**: Comprehensive health and performance reports

## 🚀 Deployment

### Production Deployment

1. **Set production environment variables**
2. **Configure Google Cloud for production**
3. **Set up reverse proxy (nginx)**
4. **Configure SSL certificates**
5. **Set up monitoring and logging**

### Docker Production

```bash
# Build production images
docker-compose -f docker-compose.prod.yml build

# Deploy with production settings
docker-compose -f docker-compose.prod.yml up -d
```

### Cloud Deployment

- **Google Cloud Run**: Serverless deployment
- **AWS ECS**: Container orchestration
- **Azure Container Instances**: Managed containers
- **Kubernetes**: Production-grade orchestration

## 🔒 Security

- **API Key Management**: Secure credential storage
- **Input Validation**: Comprehensive request validation
- **Rate Limiting**: API usage throttling
- **CORS Configuration**: Cross-origin request handling
- **Environment Isolation**: Separate dev/staging/prod configs

## 🤝 Contributing

1. **Fork the repository**
2. **Create a feature branch**
3. **Make your changes**
4. **Add tests and documentation**
5. **Submit a pull request**

### Development Guidelines

- Follow Python PEP 8 style guide
- Use TypeScript for frontend code
- Write comprehensive tests
- Update documentation for new features
- Follow conventional commit messages

## 📚 Documentation

- **API Documentation**: Available at `/docs` when backend is running
- **Code Comments**: Comprehensive inline documentation
- **Architecture Diagrams**: System design documentation
- **Troubleshooting**: Common issues and solutions

## 🆘 Support

### Getting Help

- **Documentation**: Check the `/docs` endpoint
- **Issues**: Create GitHub issues for bugs
- **Discussions**: Use GitHub discussions for questions
- **Logs**: Check system logs for debugging

### Common Issues

- **Google Cloud Setup**: Ensure APIs are enabled and credentials are correct
- **Voice Processing**: Check audio device permissions and dependencies
- **Database Issues**: Verify SQLite file permissions and paths
- **Network Issues**: Check firewall and port configurations

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Google Cloud** for AI and translation services
- **FastAPI** for the modern Python web framework
- **Next.js** for the React framework
- **Tailwind CSS** for the utility-first CSS framework
- **Agno** for AI agent orchestration

---

**Built with ❤️ using modern AI technologies to bridge communication gaps in delivery services.**

---

## 📞 Quick Commands

```bash
# Start everything
docker-compose up -d

# View logs
docker-compose logs -f

# Stop everything
docker-compose down

# Restart backend only
docker-compose restart backend

# Check status
docker-compose ps
```

**Need more help?** Check the `../others/` folder for additional documentation and setup scripts!
