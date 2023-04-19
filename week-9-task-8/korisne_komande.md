# AWS CLI naredba koja kreira CNAME zapis
aws route53 change-resource-record-sets --hosted-zone-id Z3LHP8UIUC8CDK --change-batch 
'{
    "Comment": "CREATE/DELETE/UPSERT a record ",
    "Changes": [{
        "Action": "CREATE",
        "ResourceRecordSet": {
            "Name": "denis-gobin.awsbosnia.com",
            "Type": "CNAME",
            "TTL": 60,
            "ResourceRecords": [{ "Value": "alb-denis-gobin-task-8-1474953885.us-east-1.elb.amazonaws.com"}]
}}]
}'

# terminal komande za kriranje Let's Encrypt SSL Certificata
$ sudo dnf install python3 augeas-libs
$ sudo python3 -m venv /opt/certbot/
$ sudo /opt/certbot/bin/pip install --upgrade pip
$ sudo /opt/certbot/bin/pip install certbot certbot-nginx
$ sudo ln -s /opt/certbot/bin/certbot /usr/bin/certbot
$ sudo certbot certonly --nginx # I am feeling conservative :) you can use sudo certbot --nginx instead to automatize the process

# terminal komanda datum ekspiracije certifikata
openssl s_client denis-gobin.awsbosnia.com:443 | openssl x509 -noout -dates