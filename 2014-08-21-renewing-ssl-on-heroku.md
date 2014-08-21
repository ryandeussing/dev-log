1. Generate a new private key using openssl: https://devcenter.heroku.com/articles/ssl-endpoint#generate-private-key

2. Use the private key to create a CSR: https://devcenter.heroku.com/articles/ssl-endpoint#generate-csr

3. re-key the ssl on godaddy

4. download the new certificate

5. combine the certificate file and the intermediate certificate bundle into one new .crt file

`cat bxxxe.crt gd_bundle-g2-g1.crt > bxxxe_bundle.crt`
`chmod 755 bxxxe_bundle.crt`

6. update the certificate on heroku:
https://devcenter.heroku.com/articles/ssl-endpoint#update-certificate

` heroku certs:update bxxxe_bundle.crt server.key`