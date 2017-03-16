## Security Concerns

Collection of some of the security concerns I found while searching the internet.

1. Most banks have a phone number that merchants can call and, via an automated voice response system, learn whether a particular account has enough money that a check for a particular amount will clear. Basically, you just call up, hit a few digits to go through the phone tree to the merchant check verification option, then type in the account number and the amount, and the phone system will respond with whether the account balance is at least as much as the amount you've provided.
1. IBANs: A man-in-the middle attacker may maliciously alter them to receive the money you want to pay off. So you should protect any IBAN against this threat.
1. Authorize.net has a Customer Information Manager API that allows you to store customer information in their system. It costs $20/mo. as an add-on to your account.