```bash
npm install @pipelex/sdk
```

```ts
import { PipelexApiClient } from "@pipelex/sdk";

const client = new PipelexApiClient({ apiKey: process.env.PIPELEX_API_KEY });

const result = await client.startAndWaitForResult({
  method_ref: "github.com/Pipelex/methods/invoice_extraction@v0.1.1",
  inputs: {
    document: { url: "https://example.com/invoice.pdf", mime_type: "application/pdf" },
  },
});

console.log(result.main_stuff);
```
