# Blocking DDoS Attacks: Advanced WAF Rules

Welcome to our repository dedicated to providing advanced Web Application Firewall (WAF) rules to protect your web applications from Distributed Denial of Service (DDoS) attacks. This guide includes tailored rules for different scenarios, ensuring your application stays online and secure.

## Basic WAF DDoS Rule
# Setting Up Cloudflare WAF Rules: A Visual Guide

Enhance your website's security with Cloudflare's Web Application Firewall (WAF). Follow these steps to configure WAF rules effectively:

**Open Cloudflare WAF Tutorial**
   - [![Open Cloudflare WAF Tutorial](https://i.ibb.co/R9fzKGy/cf1.jpg)](https://i.ibb.co/R9fzKGy/cf1.jpg)
   - On your Cloudflare Site, navigate to "Security" on the side tab.
   - Select "WAF."
   - Rule name (required): Enter your Rule Name - Example (BASIC WAF DDOS RULE)
   - Press "Edit Expression," Paste The Code Down Below for the Configuration
   - Choose Action to "Managed Challenge" and Press Deploy
   - Refer to this image for further assistance:
     [![Open Cloudflare WAF Tutorial 2](https://i.ibb.co/1z1cCWV/CF2.jpg)](https://i.ibb.co/1z1cCWV/CF2.jpg)

## Basic WAF DDoS Rule

This rule blocks requests from specific countries, except India, and excludes certain autonomous systems known for benign traffic.

    ```
    (ip.geoip.country ne "IN" and ip.geoip.country in {"CA", "CN", "IE", "NL", "RO", "RU", "TT", "GB", "US"} and not ip.geoip.asnum in {32934, 394699, 15169, 22577})
    ```


## WP-Admin and Cron DDoS Protection

Designed specifically for WordPress installations, this rule blocks malicious traffic targeting the wp-admin and wp-cron.php endpoints, with an exception for a trusted IP.

    ```
((http.request.uri.path contains "/wp-admin/") or (http.request.uri.path eq "/wp-cron.php")) and (ip.src ne 113.61.44.194)
    ```

## Blocking HTTP/2 DDoS Attacks

This rule targets HTTP/2 GET requests to a specific host while allowing legitimate traffic from India and excluding Googlebot and PageSpeed Insights.

    ```
(
    http.request.method eq "GET" and
    http.request.version eq "HTTP/2" and
    http.host contains "tiranga.app" and
    (
        not (
            ip.geoip.country eq "IN" and
            not (
                http.user_agent contains "Googlebot" or
                http.user_agent contains "googlebot" or
                http.user_agent contains "PageSpeed Insights"
            )
        )
    )
)
    ```

## Allow Google Bot & PageSpeed Insights

This rule ensures that requests from Google PageSpeed Insights and Googlebot are always allowed, regardless of other filtering.

    ```
    (
  (ip.src eq 162.13.83.46) and (http.user_agent contains "Google PageSpeed Insights" or "Googlebot")
)
or
(
  ip.src in {8.8.4.0/24, 8.8.8.0/24, 8.34.208.0/20, 8.35.192.0/20, 23.236.48.0/20, 23.251.128.0/19, 34.0.0.0/15, 34.2.0.0/16, 34.3.0.0/23, 34.3.3.0/24, 34.3.4.0/24, 34.3.8.0/21, 34.3.16.0/20, 34.3.32.0/19, 34.3.64.0/18, 34.4.0.0/14, 34.8.0.0/13, 34.16.0.0/12, 34.32.0.0/11, 34.64.0.0/10, 34.128.0.0/10, 35.184.0.0/13, 35.192.0.0/14, 35.196.0.0/15, 35.198.0.0/16, 35.199.0.0/17, 35.199.128.0/18, 35.200.0.0/13, 35.208.0.0/12, 35.224.0.0/12, 35.240.0.0/13, 64.15.112.0/20, 64.233.160.0/19, 66.22.228.0/23, 66.102.0.0/20, 66.249.64.0/19, 70.32.128.0/19, 72.14.192.0/18, 74.125.0.0/16, 104.154.0.0/15, 104.196.0.0/14, 104.237.160.0/19, 107.167.160.0/19, 107.178.192.0/18, 108.59.80.0/20, 108.170.192.0/18, 108.177.0.0/17, 130.211.0.0/16, 142.250.0.0/15, 146.148.0.0/17, 152.65.222.0/23, 152.65.224.0/19, 162.216.148.0/22, 162.222.176.0/21, 172.110.32.0/21, 172.217.0.0/16, 172.253.0.0/16, 173.194.0.0/16, 173.255.112.0/20, 192.158.28.0/22, 192.178.0.0/15, 193.186.4.0/24, 199.36.154.0/23, 199.36.156.0/24, 199.192.112.0/22, 199.223.232.0/21, 207.223.160.0/20, 208.65.152.0/22, 208.68.108.0/22, 208.81.188.0/22, 208.117.224.0/19, 209.85.128.0/17, 216.58.192.0/19, 216.73.80.0/20, 216.239.32.0/19, 2001:4860::/32, 2404:6800::/32, 2404:f340::/32, 2600:1900::/28, 2606:73c0::/32, 2607:f8b0::/32, 2620:11a:a000::/40, 2620:120:e000::/40, 2800:3f0::/32, 2a00:1450::/32, 2c0f:fb50::/32}
)
    ```

## Credits

### Developer

Sanji Kenneth - Sole Developer - [SanjiProject](https://github.com/SanjiProject/)

### CloudFlare

By following these steps, you'll strengthen your website's defense against potential threats. Stay secure with Cloudflare's robust WAF features!

[Cloudflare](https://dash.cloudflare.com/) | [GitHub Repository](https://github.com/SanjiProject)