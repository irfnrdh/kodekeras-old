---
title: Basic Wordpress Security hardening guide
date: 2021-04-28 11:59:00 +07:00
categories:
- Web Development
tags:
- Wordpress
layout: post
author: irfnrdh
summary: 
comment: true
---

There are lots of ways and techniques used to cover the gaps in security in wordpress. There is a good idea to do a backup first before trying to secure the wordpress you are building. The following are basic benchmarks in viewing or efforts that can be made to increase security on the wordpress, including: 

## 1. Change default administrator's username
During the installation WordPress creates a user with administrative privileges and the username 'admin'. Since usernames in WordPress cannot be changed, it is possible to try bruteforcing the password of this user to access WordPress as the administrator. This security measure creates WordPress administrator account with randomized username, and ensures that there is no user with the administrative privileges and 'admin' username. If 'admin' user is found, all content belonging to this user is reassigned to the new administrator account, and 'admin' user account is removed.

## 2. Block access to sensitive files
This security measure prevents public access to certain files that can contain sensitive information like connection credentials or various information that can be used to determine which known exploits are applicable to your WordPress website.

## 3. Change default database table prefix
WordPress database tables have the same standard names on all WordPress installations. When the standard wp_ prefix is used for the database table names, the whole WordPress database structure is transparent, making it easy for malicious scripts to obtain any data from it. This security measure changes the database table name prefix to something different than the default wp_ prefix. Note that changing database prefix on a website with production data might be dangerous, so it is strongly advised to back up your website before applying this measure.

## 4. Disable file editing in WordPress Dashboard
Disabling file editing in WordPress removes the ability to directly edit the plugin and theme file sources in the WordPress interface. This measure adds an additional layer of protection for the WordPress website in case one of WordPress admin accounts is compromised. In particular, it prevents compromised accounts from easily adding malicious executable code to plugins or themes.

## 5. Disable PHP execution in cache directories
If a compromised PHP file ends up in one of the cache directories of your website, executing it can lead to compromising the whole website. This security measure disables execution of PHP files in cache directories, preventing such exploits from happening. Note that some plugins or themes might ignore the security recommendations from WordPress Security Team and store valid PHP executables in their cache directory. You might have to disable this security measure if you need to make such plugins or themes work.

## 6. Block unauthorized access to wp-config.php
The wp-config.php file contains sensitive information like database access credentials, and so on. If, for some reason, processing of PHP files by the web server is turned off, hackers can access the content of the wp-config.php file. This security measure prevents unauthorized access to the wp-config.php file. This measure modifies the server configuration file (Apache, nginx). Note that custom directives in the .htaccess files might override this.

## 7. Block directory browsing
If directory browsing is turned on, hackers can obtain various information about your website that can potentially compromise its security. If directory browsing is turned on, this security measure can block it. This measure modifies the server configuration file (Apache, nginx). Note that custom directives in the .htaccess file might override this.

## 8. Configure security keys
WordPress uses security keys (AUTH_KEY, SECURE_AUTH_KEY, LOGGED_IN_KEY, and NONCE_KEY) to ensure better encryption of the information stored in the user's cookies. A good security key should be long (60 characters or longer), random and complex. The security check should verify that the security keys are set up and that they contain at least alphabetic and numeric characters.

## 9. Block author scans
Author scans are a form of user ID phishing. The goal of these scans is to find usernames of registered users (especially WordPress admin) and brute-force attack the login page of your website to gain access. This security measure prevents such scans from learning these usernames. Note that depending on the permalink configuration on your website this measure might prevent visitors from accessing pages that list all articles written by a particular author.

## 10. Block access to .htaccess and .htpasswd
Gaining access to .htaccess and .htpasswd files allows attackers to subject your website to a variety of exploits and security breaches. This security measure ensures that .htaccess and .htpasswd files cannot be accessed by abusers.

## 11. Block access to potentially sensitive files
This security measure prevents public access to certain files (for example, log files, shell scripts and other executables) that might exist on your WordPress website. Public access to these files could potentially compromise the security of your WordPress website.

## 12. Enable bot protection
This measure protects your website from useless, malicious or otherwise harmful bots. It blocks bots that scan your website for vulnerabilities and overload your website with unwanted requests, causing resource overuse. Note that you might want to temporarily disable this measure if you're planning to use an online service to scan your website for vulnerabilities, since these services might also use such bots.

## 13. Enable hotlink protection
Hotlink protection prevents other websites from displaying, linking or embedding your images. This practice is called hotlinking, add it can quickly drain your bandwidth and make your website unavailable.

## 14. Turn off pingbacks
Pingbacks allow other WordPress websites to automatically leave comments under your posts when these websites link to these posts. Pingbacks can be used to launch DDoS attacks on your website. This security measure turns off XML-RPC pingbacks for your whole website and also disables pingbacks for previously created posts with pingbacks enabled.

## 15. Disable scripts concatenation for WordPress admin panel
This security measure turns off concatenation of scripts running in the WordPress Administrator panel, preventing your website from being affected by certain DoS attacks. Turning off concatenation of scripts might slightly affect the performance of WordPress Administrator panel, but it should not affect your WordPress website from visitors' point of view.

## 16. Forbid execution of PHP scripts in the wp-content/uploads directory
The wp-content/uploads directory may contain insecure PHP files that can be executed to take over and exploit your website. This security measure prevents the execution of PHP files in the wp-content/uploads directory. This measure modifies the server configuration file (Apache, nginx). Note that custom directives in the .htaccess files might override this.

## 17. Forbid execution of PHP scripts in the wp-includes directory
The wp-includes directory may contain insecure PHP files that can be executed to take over and exploit your website. This security measure prevents the execution of PHP files in the wp-includes directory. This measure modifies the server configuration file (Apache, nginx). Note that custom directives in the .htaccess file might override this.

## 18. Restrict access to files and directories
If access permissions for files and directories are not secure enough, these files can be accessed by hackers and used to compromise your website. This security measure sets the permissions for the wp-config file to 600, for other files to 644, and for directories to 755.

continued...