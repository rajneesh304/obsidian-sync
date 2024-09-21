- [ ] Footer
	- [ ] Events
	- [ ] Memberships
	- [ ] mail:to
- [ ] Analytics -- Pixel 



ref. 
1. https://www.peppermint-it.au/
2. https://www.benetics.io/blog

Checkout: 
Glass effect: https://www.awwwards.com/inspiration_search/?text=scrolling-through-product-features-lampa


Buildabang Machine:
```bash
ssh -i $HOME/Downloads/ssh-key-2024-09-14.key ubuntu@152.67.6.34
```

Install nvm:
https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-20-04#option-3-installing-node-using-the-node-version-manager

remote ssh config: 
```
Host buildabang
	HostName 152.67.6.34
	User ubuntu
	IdentityFile /home/zero/Downloads/ssh-key-2024-09-14.key
```

Nextjs references: 
1. https://github.com/vercel/next.js/tree/canary/examples/with-docker
2. https://nextjs.org/docs/pages/building-your-application/deploying#docker-image
3. https://stackoverflow.com/questions/74185594/how-to-deploy-a-next-js-app-on-https-ssl-connection-with-docker


### Certificate setup
```bash
sudo apt update 
sudo apt install certbot python3-certbot-nginx
sudo certbot certonly --standalone -d your-domain.com -d www.your-domain.com

```
Certificate location: 
```
Certificate is saved at: /etc/letsencrypt/live/rajneesh.dev/fullchain.pem  
Key is saved at:         /etc/letsencrypt/live/rajneesh.dev/privkey.pem
```

### Not able to connect to nextjs app from nginx docker
1. fuck oracle: https://stackoverflow.com/questions/62326988/cant-access-oracle-cloud-always-free-compute-http-port #fuck-oracle 
```bash
sudo apt-get install firewalld
sudo systemctl enable firewalld
sudo systemctl start firewalld


sudo firewall-cmd --zone=public --add-port=80/tcp --permanent  #  or --add-service=http 
sudo firewall-cmd --reload

```