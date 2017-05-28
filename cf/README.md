1## Cloud Foundry

  cf login -a https://api.bosh-lite.com --skip-ssl-validation -u admin -p admin
  cf create-org drnic
  cf create-space space -o drnic
  cf target -o drnic -s space
  cf create-service-broker cf-rabbitmq-release p1-rabbit p1-rabbit-devpwd http://ha-rabbitmq-broker.bosh-lite.com
  cf enable-service-access rabbitmq-36
  cf create-service rabbitmq-36 standard rmq

cf push

cf bind-service test-app rmq

cf unbind-service test-app rmq

CF_TRACE=true <cmd>

cf create-service-broker cf-rabbitmq-release p1-rabbit p1-rabbit-devpwd http://ha-rabbitmq-broker.svc.asv.ice.gecis.io

https://p-ha-rabbitmq-broker.system.asv-stg.ice.predix.io

cf purge-service-offering ha-rabbitmq

## Security Groups

### debugging nats
nats sub -s nats://<nats-user>:<nats-password>@<host>:4222 router.register

### test for tcp/udp traffic from cf
https://github.com/pivotalservices/cf-egress-tester

curl -k https://egress-test.run.asv-sb.ice.predix.io/egress-status/tcp/rabbitmq-sb.svc.asv.ice.gecis.io/5672

## pcf
### root ca location
/var/tempest/workspaces/default/root_ca_certificate
