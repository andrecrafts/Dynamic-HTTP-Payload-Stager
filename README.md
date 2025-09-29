# Dynamic HTTP(S) Payload-Stager

### **A dynamic HTTP/S stager that lets one shellcode loader be reused for different encrypted payloads - no rebuilds.**

Learn more about this in my [blog post](https://wafflesexploits.github.io/posts/Dynamic-HTTP-Payload-Stager/)

## Quick overview
A Python tool packages decryption params (key, IV, etc.) into a Base64 file you host. The stager fetches that file at runtime, parses `<name><delimiter><hex>` lines, converts hex -> bytes, and loads them into memory.

This lets the same loader decrypt different payloads on demand - no rebuilding or redeploying required.


## Code
- [ConvertToFormat.py](https://github.com/WafflesExploits/Dynamic-HTTP-Payload-Stager/blob/main/ConvertToFormat.py)
- [Dynamic_HTTP_Payload_Stager.cpp](https://github.com/WafflesExploits/Dynamic-HTTP-Payload-Stager/blob/main/Dynamic_HTTP_Payload_Stager.cpp)

## Video Demo
[Video Demo](https://wafflesexploits.github.io/assets/video_demo_http-stager.mp4)

## Update
`ConvertToFormat.py` now supports: read-from-file, custom delimiter, and output path.

<img src="https://github.com/user-attachments/assets/47e65913-a8c8-4f21-81ac-12834258b8cc" width="601" height="169">

## Notes
- Host the file over HTTPS; consider token/HMAC or short-lived URLs for integrity.  
- Stager should validate counts/lengths and Base64 decode success.  
- PoC - treat keys/hosting with OPSEC in mind.
