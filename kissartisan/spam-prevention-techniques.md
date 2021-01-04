## Honeypot
1. Hidden field
 - Create a hidden field, then if that field has value, then it is a **SPAM**.
 - Or if that hidden field is not included in the request, then it is still a **SPAM**.
2. Time field
 - Create a hidden field that has a value of the current time when the browser is loaded.
 - Then compare that field to how long does it take for the form to be submitted.
 - If it is less than the time you expected to be filled (for example 3 seconds), then it is a **SPAM**.

Relevant URL: https://laracasts.com/series/spam-prevention-techniques
