# Wordpress Pentesting Tools

## [wpscan](https://wpscan.com/wordpress-security-scanner)

* For all plugins with known vulnerabilities:  
    ```wpscan --url example.com -e vp --plugins-detection mixed --api-token YOUR_TOKEN```

* For all plugins in our database (could take a very long time):  
    ```wpscan --url example.com -e ap --plugins-detection mixed --api-token YOUR_TOKEN```

* Password brute force attack:  
    ```wpscan --url example.com -e u --passwords /path/to/password_file.txt```
