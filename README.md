# packer-drachtio-freeswitch

A [packer](https://www.packer.io/) template to build an AMI for a customized version of freeswitch for use with [drachtio-fsmrf](https://www.npmjs.com/package/drachtio-fsmrf)

## Installing 

```
$ git clone git@github.com:davehorton/packer-drachtio-freeswitch.git
$ cd packer-drachtio-freeswitch
$ git submodule update --init --recursive
$  packer build  \
-var 'aws_access_key=YOUR-ACCESS-KEY'  \
-var 'aws_secret_key=YOUR-SECRET-KEY' \
template.json
```

### variables
These variables can be specified on the `packer build` command line.  Defaults are listed below, where provided.
```
"aws_access_key": ""
```
Your aws access key.
```
"aws_secret_key": ""
```
Your aws secret key.

```
"region": "us-east-1"
```
The region to create the AMI in

```
"source_ami": "ami-024a64a6685d05041"
```
Source AMI to use.

```
ssh_username": "ubuntu"
```
ssh username to use when connecting to instance for provisioning

```
"ami_description": "EC2 AMI rtpengine Ubuntu 18.04"
```
AMI description.

```
"instance_type": "t2.medium"
```
EC2 Instance type to use when building the AMI.

```
"cloud_provider": "aws"
```
Cloud provider the AMI will be built on.

```
"freeswitch_version": "v1.8.5"
```
The version of freeswitch to build

```
"sip_port": "5060"
```
SIP port that freeswitch will listen on

```
"dtls_sip_port": "5061"
``` 
DTLS SIP port that freeswitch will listen on

```
"build_with_grpc": "false"
```
if true, build mod_google_transcribe, mod_google_tts, and mod_dialogflow.
Note: regardless of this setting, mod_audio_fork is always built

```
"freeswitch_bind_cloud_ip": "true"
``` 
If true, set Freeswitch external sip and rtp addresses to public IP assigned by the cloud provider, otherwise bind to the local ipv4 address
