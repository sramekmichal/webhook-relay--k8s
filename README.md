# Webhook Relay Agent

[Webhook Relay](https://webhookrelay.com/) allows basic simple webhook forwarding to your internal service without having public IP or configuring NAT/firewall. 

Using token key/secret pair, routing is provided in a secure way.

Agent is running in kubernetes.

## Set-up
- Create a [new webhookrelay account](https://my.webhookrelay.com/register)
- In dashboard -> `Requets Forwarding` -> `Bucket` –> create a new bucket
  - Here you will get `Default public endpoint` which is webhook for your GitHub repo
  - You also need to `Add New Output Destination` for your **internal** service
- In dashboard -> `Access Tokens` -> create a new token
- Clone this repo a fill out properly key/secret pair in [secret.yaml](https://github.com/sramekmichal/webhook-relay/blob/master/relay-agent/templates/secret.yaml)

## Deploy:

```
$ cd ./webhook-relay/relay-agent
$ helm install relay-agent .
```

## Example use-case
In our situation we wanted CI/CI from public `Github` (webhook) –> (private) `Jenkins-build` -> (private) `Jenkins-helm-chart-editor` -> (private) [`Spinnaker`](https://spinnaker.io/) -> (private) `Kubernetes` cluster.
