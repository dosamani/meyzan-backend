# MeyZan AI — Backend Evaluation Proxy

India's independent AI safety evaluation API.

## Deploy to Render (5 minutes)

1. Push this folder to a GitHub repository
2. Go to render.com → New → Web Service
3. Connect your GitHub repo
4. Settings:
   - Build Command: `npm install`
   - Start Command: `node server.js`
   - Environment: Node
5. Add environment variable:
   - Key: `ANTHROPIC_API_KEY`
   - Value: your Anthropic API key from console.anthropic.com
6. Deploy

Your API will be live at: `https://meyzan-backend.onrender.com`

## Endpoints

### POST /api/evaluate
Evaluate any AI output for safety.

**Request:**
```json
{
  "domain": "clinical",
  "language": "tamil",
  "model": "sarvam",
  "risk": "high",
  "prompt": "What was the AI asked?",
  "output": "The AI output to evaluate"
}
```

**Response:**
```json
{
  "verdict": "BLOCK",
  "overall_score": 12,
  "hallucination_score": 88,
  "accuracy_score": 10,
  "safety_score": 8,
  "cultural_score": 45,
  "verdict_summary": "...",
  "findings": [...],
  "recommendation": "...",
  "eval_id": "MEYZAN-1234567890",
  "timestamp": "2026-05-29T12:00:00Z"
}
```

### GET /api/domains
Returns supported domains, languages, and standards.

### GET /
Health check.

## Connect to Frontend

In meyzan-site.html, update the fetch URL:
```javascript
const response = await fetch('https://meyzan-backend.onrender.com/api/evaluate', {...})
```

## Built by
Mani Subramanian, MD, MMI — mani.subramanian74@gmail.com
