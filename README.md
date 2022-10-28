# Cloudformation-CFN-HUB
Cloudformation template to update the host file in any EC2 instances started by an AutoScaling Group

We can define several files that contain hooks monitoring several resources. Let’s examine the hook defined in /etc/cfn/hooks.d/cfn-auto-reloader.conf.

This hook monitors  Resources.EcsInstanceLaunchConfiguration.Metadata.AWS::CloudFormation::Init,  

so any changes to the metadata of this launch configuration. When anything changes, it executes the command /opt/aws/bin/cfn-init --verbose --stack=${AWS::StackName} --region=${AWS::Region} --resource=EcsInstanceLaunchConfiguration --configsets UpdateEnvironment

Which updates the host file with the private IP address of the Graylog instance.
