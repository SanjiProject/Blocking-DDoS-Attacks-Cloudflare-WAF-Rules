# Blocking DDoS Attacks: Advanced WAF Rules With CloudFlare

Welcome to my repository dedicated to providing advanced Web Application Firewall (WAF) rules to protect your web applications from Distributed Denial of Service (DDoS) attacks. This guide includes tailored rules for different scenarios, ensuring your application stays online and secure.

## Basic WAF DDoS Rule
# Setting Up Cloudflare WAF Rules: A Visual Guide

Enhance your website's security with Cloudflare's Web Application Firewall (WAF). Follow these steps to configure WAF rules effectively:

**Open Cloudflare WAF Tutorial**
     [![Open Cloudflare WAF Tutorial](https://i.ibb.co/R9fzKGy/cf1.jpg)](https://i.ibb.co/R9fzKGy/cf1.jpg)
   - On your Cloudflare Site, navigate to "Security" on the side tab.
   - Select "WAF."
   - Rule name (required): Enter your Rule Name - Example (BASIC WAF DDOS RULE)
   - Press "Edit Expression," Paste The Code Down Below for the Configuration
   - Choose Action to "Managed Challenge" and Press Deploy
   - Refer to this image for further assistance:
     [![Open Cloudflare WAF Tutorial 2](https://i.ibb.co/1z1cCWV/CF2.jpg)](https://i.ibb.co/1z1cCWV/CF2.jpg)

## Blocking HTTP/2 DDoS Attacks

This rule targets HTTP/2 GET requests to a specific host while allowing legitimate traffic from India and excluding Googlebot and PageSpeed Insights.


    (http.request.version eq "HTTP/2" and http.request.method eq "GET" and not ip.geoip.country in {"IN" "PH"})


## WP-Admin and WP-Cron DDoS Protection

Designed specifically for WordPress installations, this rule blocks malicious traffic targeting the wp-admin and wp-cron.php endpoints, with an exception for a trusted IP.

    ((http.request.uri.path contains "/wp-admin/" or http.request.uri.path eq "/wp-cron.php") and not ip.src eq 113.61.44.194)


## Allow Google Bot & PageSpeed Insights For SEO Purposes

This rule ensures that requests from Google PageSpeed Insights and Googlebot are always allowed, regardless of other filtering.

    (http.user_agent eq "Googlebot") or (http.user_agent eq "googlebot") or (http.user_agent eq "Chrome-Lighthouse")

Dont forgot to Select Skip And Checklist on "All Remaining Custom Rules"

 [![Open Cloudflare WAF Tutorial 3](https://i.ibb.co/Pj9c5S6/cf3.jpg)](https://i.ibb.co/Pj9c5S6/cf3.jpg)

## Set Rate Limit on Your WAF

- On your Cloudflare Site, navigate to "Security" on the side tab.
- Select "WAF."
 [![Open Cloudflare WAF Tutorial 4](https://i.ibb.co/hFBCkSb/cf3.jpg)](https://i.ibb.co/hFBCkSb/cf3.jpg)
- Choose Rate Limiting Rules 
- Create Rule
- Rule name (required): Enter your  Desired Rule Name - Example (Rate Limit)
- Field Choose URI Path 
- Operator Choose equals
- Value use "/"
- When rate Exceeds request you may choose 10 my recommendation is 5 
- Period 10 Seconds 
- Choose Action "Block"
- Duration you may choose "1 Minute" for Pro Plan and "10 Seconds" with Free Plan
 [![Open Cloudflare WAF Tutorial 4](https://i.ibb.co/D9yr56c/cf4.jpg)](https://i.ibb.co/D9yr56c/cf4.jpg)

## Credits

### Developer

Sanji Kenneth - Sole Developer - [SanjiProject](https://github.com/SanjiProject/)

### CloudFlare

By following these steps, you'll strengthen your website's defense against potential threats. Stay secure with Cloudflare's robust WAF features!

[Cloudflare](https://dash.cloudflare.com/) | [GitHub Repository](https://github.com/SanjiProject)