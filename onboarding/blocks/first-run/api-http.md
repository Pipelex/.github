```bash
curl -s https://api.pipelex.com/v1/start \
  -H "Authorization: Bearer $PIPELEX_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "method_ref": "github.com/Pipelex/methods/invoice_extraction@v0.1.1",
    "inputs": {"document": {"url": "https://example.com/invoice.pdf", "mime_type": "application/pdf"}}
  }'
# 202 → {"pipeline_run_id": "..."}

RUN_ID=...     # the pipeline_run_id the start returned
curl -s https://api.pipelex.com/v1/runs/$RUN_ID/results \
  -H "Authorization: Bearer $PIPELEX_API_KEY"
```

The start returns immediately and the run is durable — poll the results route, or fetch them hours later by the same id. The document URL is a placeholder: point it at a file of your own that Pipelex can reach over HTTPS.
