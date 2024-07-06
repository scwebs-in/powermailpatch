# TYPO3 Extension Patch for Powermail

This PATCH  allows you to configure separate SMTP setting for each domain

on a large enterprise, that manages multiple domains
    - it is not easy to setup separate SMTP setting for each domain
    - You can use the "TYPOSCRIPT Config" in each domain or on each page!

NOTE: Implicit TLS encryption is enabled by default

# How to apply the PATCH?

STEPS:

* Replace the SendMailService.php file located in typo3conf/ext/powermail/Classes/Domain/Service/Mail/SendMailService.php
* Copy the file SendPhpMaierlService.php to the folder typo3conf/ext/powermail/Classes/Domain/Service/Mail/
* Add the PHPMailer folder to typo3conf/ext/powermail/Classes/Domain/Service/
* Copy the TYPOSCRIPT Config Example to the SETUP section of the root Typoscript
* make sure the SMTP info like host, username, password, from and from name are set properly

SEND a mail and TEST - it should work smoothly

You can use the "TYPOSCRIPT Config" given below on each domain or on each page!

## TYPOSCRIPT Config Example:

plugin.tx_powermail {
    settings {
        setup {
            mailer {
                smtp_host = smtp.gmail.com
                smtp_auth = true
                smtp_username = 
                smtp_password = 
                smtp_port = 465
                mailer_from = name@example.com
                mailer_from_name = 
            }
        }
    }
}

# Note on PHPMailer

This patch Uses PHPMailer 6.8.1 - As of July 6 2024
This PHPMailer is Compatible with PHP 5.5 and later, including PHP 8.2

# Patch tested on

* TYPO3 11.5.24
* Powermail 10.7.0

* TYPO3 10.4.37
* Powermail 8.4.2

# COMING SOON
A new extension - which works without a PATCH
Support for TYPO3 v12 & TYPO3 v13