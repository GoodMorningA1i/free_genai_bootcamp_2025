## Pull a model
```
curl http://localhost:8008/api/pull -d '{
  "model": "llama3"
}'
```

## Generate a request
```
curl http://localhost:8008/api/generate -d '{
  "model": "llama3",
  "prompt":"Why is the sky blue?"
}'
```