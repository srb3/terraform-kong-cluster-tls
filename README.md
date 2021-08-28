# terraform-kong-cluster-tls

A terraform module for creating tls certificates for use in
kong gateway shared mode clustering

## Usage

### Using module defaults

The following will create the correctly formed
certificate and key to use with all instances of
a Kong cluster using shared mode clustering

```HCL
module "tls" {
  source   = "srb3/tls/kong-cluster"
}
...
...
...
# example of usage
module "kong-install" {
  source               = "../../"
  hosts                = [module.ec2_instance.public_ip]
  ssh_user_name        = "ec2-user"
  ssh_user_private_key = "~/.ssh/id_rsa"
  cluster_cert         = module.tls.cert.kong-cluster.cert_pem
  cluster_cert_key     = module.tls.key.kong-cluster.private_key_pem
  kong_config          = local.kong_config
}
```

## Testing

no testing yet
