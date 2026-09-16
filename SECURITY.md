# Security

Public workflows must contain no debtor data or production secrets. Use a fine-grained read-only token limited to the private SmartColl source repository. Configure Apps Script URL, Apps Script shared secret, and app bearer token only in Cloudflare Pages project secrets; never as Vite variables. Rotate any token accidentally printed or committed.
