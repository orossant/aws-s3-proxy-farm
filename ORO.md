# mode d'emploi pour deployer


cd aws-s3-proxy-farm/  
cd example/  
npm i @aws-cdk/aws-ec2  
npm i @aws-cdk/aws-s3-deployment  
cdk synth  
cdk bootstrap   
cdk deploy  


cdk destroy




Remarques : 

1 instance ec2 deployée en zone privée avec un networkloadbalancer en front , 
asg, target group, multi-az, igw, nat-gw, vpc-endpoint type gateway pour S3
userdata : installation et conf du proxy nginx d'ou le besoin de NAT-GW, mais evitable avec une ami pre-configurée
instance installe reverse-proxy nginx accessible depuis subnet config (par defaut 0.0.0.0 mais normalement mettre le subnet onprem)


Variante : remplacer vpc-endpoint GW pour S3 par une vpc-endpoint interface (private link)
maintenant supporté