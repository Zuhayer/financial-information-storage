# Best practices for storing Financial information in a database

The crux of all the information on the internet regarding this topic, which I was able to dig up is:

- Don't do it.
- The legal and financial implications will be disastrous.
- Look for established PCI compliant third party solutions or hire an expert.
- Never store any sensitive information on a shared server.

## But if you have no other choice

- Research the laws that govern your countries financial institutions.
- Research for the most appropriate security mechanism.
    - Protect the [Securing Server](https://www.symantec.com/products/endpoint-hybrid-cloud-security/hybrid-cloud-security/data-center-server), [Securing Database](https://www.symantec.com/connect/articles/securing-mysql-step-step), Data Transportation, Internal Threats
    - SSL certificate to provide a layer of security, prevent MITM (Man in the middle) attacks.
    - Research for the most appropriate encryption mechanism.

## Established 3rd Party Solutions

- https://developer.paypal.com
- http://developer.authorize.net
- https://www.spreedly.com/

I, having a requirement to store the user information, implemented it as follows:

## How I did it:

```sql
CREATE TABLE `Bank` (
    `id`  int(11) NOT NULL AUTO_INCREMENT ,
    `user_id`  int(11) NOT NULL ,
    `bank_name`  varchar(255) CHARACTER SET latin1 COLLATE latin1_swedish_ci NULL DEFAULT NULL ,
    `bank_branch`  varchar(255) CHARACTER SET latin1 COLLATE latin1_swedish_ci NULL DEFAULT NULL ,
    `bank_account_title`  varchar(255) CHARACTER SET latin1 COLLATE latin1_swedish_ci NULL DEFAULT NULL ,
    `bank_account_number`  varchar(255) CHARACTER SET latin1 COLLATE latin1_swedish_ci NULL DEFAULT NULL ,
    `bank_account_iban`  varchar(34) CHARACTER SET latin1 COLLATE latin1_swedish_ci NULL DEFAULT NULL ,
    `bank_swiftcode`  varchar(11) CHARACTER SET latin1 COLLATE latin1_swedish_ci NULL DEFAULT NULL ,
    `enabled`  tinyint(1) NOT NULL DEFAULT 1 ,
    `is_deleted`  tinyint(1) NOT NULL DEFAULT 0 ,
    `created_date`  datetime NULL DEFAULT NULL ,
    `modified_date`  datetime NULL DEFAULT NULL ,
    PRIMARY KEY (`id`),
    FOREIGN KEY (`user_id`) REFERENCES `fos_user` (`id`) ON DELETE RESTRICT ON UPDATE RESTRICT,
    INDEX `fos_user_ibfk_id_1` (`user_id`) USING BTREE
)
    ENGINE=InnoDB
    DEFAULT CHARACTER SET=latin1 COLLATE=latin1_swedish_ci
    AUTO_INCREMENT=1
    ROW_FORMAT=DYNAMIC;
```

p.s. This is just a generic look at 'Best practices for storing Financial information'. I have searched for two whole days and have not been able to find much meaning full details. I will keep updating this repo as i learn good, better, best practices overtime.