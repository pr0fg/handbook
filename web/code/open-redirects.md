# Open Redirects

Unvalidated redirects and forwards are possible when a web application accepts untrusted input that could cause the web application to redirect the request to a URL contained within untrusted input. By modifying untrusted URL input to a malicious site, an attacker may successfully launch a phishing scam and steal user credentials.

## Full List of Vectors
[View GitHub Gist](https://gist.github.com/pr0fg/49657b8a5249a3232d69e7d50e822664)

## Vulnerable Code Examples

Java:
```
response.sendRedirect(request.getParameter("url"));
```

PHP:
```
$redirect_url = $_GET['url'];
header("Location: " . $redirect_url);
```

C#.NET:
```
string url = request.QueryString["url"];
Response.Redirect(url);
```

Rails:
```
redirect_to params[:url]
```