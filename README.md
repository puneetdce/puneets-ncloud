Details and paramters required by Cloudformation tmpl - 

	BastionKeyName - Key for NAT server 
	KeyName - Key for server access 
	BastionInstanceType - Server type for Instance in etcd_layer
	NATInstanceType - NAT server type 

Subnets - 

	VPC - "10.0.0.0/16"
	Public Subnet - "CIDR": "10.0.0.0/24"
	Private Subnet - "CIDR": "10.0.1.0/24"

Security groups -

	NATSecurityGroup - Internet gateway is associated with this . 
	EtcdSecurityGroup - Opening etcd port from outside word. 

IAM user - 

	Role - WebServerRole 
		WebServerRolePolicy :
			"Effect": "Allow",
            "NotAction": "iam:*",
            "Resource": "*"

OpsWork - 

	Stacks - 

		1) opsStack
			a) Layers -
				i) etcdLayer
					This layer is is getting created with etcd cookbook . Setting key foo key with the certs. 

There are 2 cookbook -
	
	1) puneets-etcd-cookbook 
		This is main cookbook which is calling confd cookbook and setting up keys with cert as value . 
		More details - https://github.com/puneetdce/puneets-etcd-cookbook
	2) puneets-confd-cookbook 
		Details on - https://github.com/puneetdce/puneets-confd-cookbook

