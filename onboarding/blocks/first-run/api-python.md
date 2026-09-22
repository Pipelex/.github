```bash
pip install pipelex-sdk
```

```python
from pipelex_sdk.client import PipelexAPIClient

async with PipelexAPIClient() as client:
    result = await client.start_and_wait(
        method_ref="github.com/Pipelex/methods/invoice_extraction@v0.1.1",
        inputs={"document": {"url": "https://example.com/invoice.pdf", "mime_type": "application/pdf"}},
    )
    print(result.main_stuff)
```
