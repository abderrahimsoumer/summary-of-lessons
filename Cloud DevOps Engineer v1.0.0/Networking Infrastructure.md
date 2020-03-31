## Workflow and Helpers
When creating your `.yml` file remember that using the `Description Field` is optional. Here we start by adding a short description of our name and project we are working on.
```YAML
Description: >
    Carlos Rivas / Udacity 2019
```
### #### Recommended best practices
Although descriptions are optional , `Resource` fields are required. Remember to include **at least one resource** (e.g., a VPC, an EC2 instance, a database) in the CloudFormation `.yml` script, otherwise it will give an error when you try to run the script..
```YAML
Resources:
    VPC:
        TYPE: AWS::EC2::VPC
```
#### Practice Fixing Errors
  - Practice fixing errors, as this will help you prepare for real scenarios on the job. 
  - For instance, try altering correct, working yml scripts to see if they generate an error. 
  - Practice reading error messages to understand what caused the error, and how to fix them.
#### Common commands used
Common commands we’ll use are `aws cloudformation create-stack`, and `aws cloudformation update-stack`.

## #### Connecting VPC's & Internet Gateways
It's important to note when connecting an `Internet Gateway` to a `VPC`, we need to define an additional resource called `InternetGatewayAttachment`. This attachment references both the VPC and the InternetGateway. Here is the syntax for the following connection:

```YAML
Type: AWS::EC2::VPCGatewayAttachment
Properties: 
  InternetGatewayId: String
  VpcId: String
  VpnGatewayId: String
```
## ### Don't hard-code parameters
Avoid hard coding parameter values. Instead, use a separate parameter file to store parameter values. Note that the parameter file should be in `.json` format, as `.yml` format is not yet supported for the parameter file.
Here is an example parameters file from `network-parameters.json` which is holding key-value pairs for the `Environment` & `VpcCiIDR`.

```JSON
[
    {
        "ParameterKey": "EnvironmentName",
        "ParameterValue": "UdacityProject"
    },
    {
        "ParameterKey": "VpcCIDR",
        "ParameterValue": "10.0.0.0/16"
    }
]
```
### #### Setting Parameters
`Parameters` should be declared above your `Resources`:
```YAML
Parameters:
# whatever you consider a changing value, put it as a parameter instead of hard-coding it into your script
Resources:
```
and should follow the general format of: 
```YAML
Parameters:
  ParameterLogicalID:
    Type: DataType
    ParameterProperty: value
```
Here we set the `EnvironmentName` parameter in our sample code from the video:
```YAML
Parameters:
    EnvironmentName:
        Description: An Environment name that will be prefixed to resources
        Type: String
```
### #### Default Parameters
You can also provide default values for parameters in case one was not passed in. In this example you can see that `VpcCIDR` has a default value of `10.0.0.0/16`.

```YAML
Parameters:
    EnvironmentName:
        Description: An Environment name that will be prefixed to resources
        Type: String

    VpcCIDR:
        Description: Please enter the IP range (CIDR notation) for this
        Type: String
        Default: 10.0.0.0/16
```
#### Calling CloudFormation
When calling AWS CloudFormation, you’ll pass in the name of the `.yml` file as well as the name of the parameter file as parameters to the CloudFormation call. 

For example:

`aws cloudformation create-stack --stack-name MyStack --template-body file://MyCloudformationScript.yml  --parameters file://MyEnvironmentVariables.json `

- Note that CloudFormation knows to create the resources in order, based on their dependencies (VPC and InternetGateway, before creating the InternetGatewayAttachment).
#### #### Further Resources
  - The `network.yml` file that I use in this lesson is included in the Resources tab in the left sidebar of this page, if you'd like to download it.
  - [Parameters](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/parameters-section-structure.html)
  - [VPC](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-vpc.html) 
  - [VPCCidrBlock](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-vpccidrblock.html) 
  - [Internet Gateway](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-internetgateway.html)
### #### Adding Subnets
To specify a `Subnet` for your `VPC` you use the following syntax: 
```YAML
Type: AWS::EC2::Subnet
Properties: 
  AssignIpv6AddressOnCreation: Boolean
  AvailabilityZone: String
  CidrBlock: String
  Ipv6CidrBlock: String
  MapPublicIpOnLaunch: Boolean
  Tags: 
    - Tag
  VpcId: String
```
Here is the actual setup of our 2 private `Subnets`:

```YAML
PrivateSubnet1
    Type: AWS::EC2::Subnet
    Properties:
        VpcId: !Ref VPC
        AvailabilityZone: !Select [ 0, !GetAZ's '' ]
        CirderBlock: !Ref PrivateSubnet1CIDR
        MapPublicIpOnLaunch: false
        Tags: 
            -   Key: Name
                Value: !Sub ${EnvironmentName} Private Subnet (AZ1)

PrivateSubnet2
    Type: AWS::EC2::Subnet
    Properties:
        VpcId: !Ref VPC
        AvailabilityZone: !Select [ 1, !GetAZ's '' ]
        CirderBlock: !Ref PrivateSubnet1CIDR
        MapPublicIpOnLaunch: false
        Tags: 
            -   Key: Name
                Value: !Sub ${EnvironmentName} Private Subnet (AZ2)
```



You can see the index being used from the returning `AvailabilityZone's` array. Notice that our subnets **are not** sharing `AvailabilityZones`. We are keeping them separated like we displayed in our diagrams from the previous lesson:

PrivateSubnet1: `AvailabilityZone: !Select [ 0, !GetAZ's '' ]`

PrivateSubnet2: `AvailabilityZone: !Select [ 1, !GetAZ's '' ]`

This code:
`!select [0, !GetAZs‘’]`


calls the function GetAZ, which returns a list of availability zones, which are indexed 0, 1 etc. 
##### Tip
  - Name your subnets using tags, to keep track when you create many subnets.

## ### Adding a NAT Gateway

You can use `NAT Gateways` in both your public and/or private `Subnets`. The following code is the basic syntax for declaring a `NAT Gateway`:
```YAML
Type: AWS::EC2::NatGateway
Properties: 
  AllocationId: String
  SubnetId: String
  Tags: 
    - Tag
```
The following declarations are from the sample code shown in the above video:

```YAML
NatGateway1EIP:
        Type: AWS::EC2::EIP
        DependsOn: InternetGatewayAttachment
        Properties: 
            Domain: vpc

    NatGateway2EIP:
        Type: AWS::EC2::EIP
        DependsOn: InternetGatewayAttachment
        Properties:
            Domain: vpc

    NatGateway1: 
        Type: AWS::EC2::NatGateway
        Properties: 
            AllocationId: !GetAtt NatGateway1EIP.AllocationId
            SubnetId: !Ref PublicSubnet1

    NatGateway2: 
        Type: AWS::EC2::NatGateway
        Properties:
            AllocationId: !GetAtt NatGateway2EIP.AllocationId
            SubnetId: !Ref PublicSubnet2
```



The `EIP` in `AWS::EC2::EIP` stands for Elastic IP. This will give us a known/constant IP address to use instead of a disposable or ever-changing IP address. This is important when you have applications that depend on a particular IP address. `NateGateway1EIP` uses this type for that very reason:
```YAML
 NatGateway1EIP:
        Type: AWS::EC2::EIP
        DependsOn: InternetGatewayAttachment
        Properties: 
            Domain: vpc
```
##### Tip
  - Use the `DependsOn` attribute to protect your dependencies from being created without the proper requirements.
In the scenario above the `EIP` allocation will only happen after the `InternetGatewayAttachment` has completed.

##### #### Resources
  - [Subnet Resource Documentation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-subnet.html)
  - [DependsOn Attribute](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-attribute-dependson.html)
  - [Creating NAT Gateways](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html#nat-gateway-creating)
  - [NAT Gateway Resource Documentation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-natgateway.html)

### Glossary
**Routing:** Routing is the action of applying routing rules to your network, in this case, to your VPC. 
Routing rule: Resources follow the routing rule, which defines what resource has access to communicate with another resource. It blocks traffic from resources that do not follow the routing rule.

## #### Route Tables
We create `RouteTables` for `VPC`s so that we can add `Routes` that we later associate with `Subnets`. The following is the syntax used to define a `RouteTable`:
```YAML
Type: AWS::EC2::RouteTable
Properties: 
  Tags: 
    - Tag
  VpcId: String
```
The only required property for setting up a `RouteTable` is the `VpcId`. Here is an example table from the video lesson:
```YAML
PublicRouteTable:
        Type: AWS::EC2::RouteTable
        Properties: 
            VpcId: !Ref VPC
            Tags: 
                - Key: Name 
                  Value: !Sub ${EnvironmentName} Public Routes
 ```
 ### #### Routes
The following is the syntax used to set up our `Route`:
```YAML
Type: AWS::EC2::Route
Properties: 
  DestinationCidrBlock: String
  DestinationIpv6CidrBlock: String
  EgressOnlyInternetGatewayId: String
  GatewayId: String
  InstanceId: String
  NatGatewayId: String
  NetworkInterfaceId: String
  RouteTableId: String
  VpcPeeringConnectionId: String
```
The `DestinationCidrBlock` property is used for destination matching and a `wildcard address` (`0.0.0/0`) to reference all traffic. So in the following example, when we use the wildcard address `0.0.0.0/0`, we are saying for any address that comes through this route, send it to the referenced `GatewayId`: 
```YAML
DefaultPublicRoute: 
        Type: AWS::EC2::Route
        DependsOn: InternetGatewayAttachment
        Properties: 
            RouteTableId: !Ref PublicRouteTable
            DestinationCidrBlock: 0.0.0.0/0
            GatewayId: !Ref InternetGateway
 ``` 
 ### #### SubnetRouteTableAssociation
In order to associate `Subnets` with our `Route Table` we will need to use a `SubnetRouteTableAssociation`. `SubnetRouteTableAssociations` are defined using the following syntax:
```YAML
Type: AWS::EC2::SubnetRouteTableAssociation
Properties: 
  RouteTableId: String
  SubnetId: String
```
This only takes two properties, which are the id's used for our `RouteTable` and our `Subnet`. You can see references used in the example from our video lesson above:  

```YAML
PublicSubnet1RouteTableAssociation:
        Type: AWS::EC2::SubnetRouteTableAssociation
        Properties:
            RouteTableId: !Ref PublicRouteTable
            SubnetId: !Ref PublicSubnet1
``` 
**Important Note:** `Routes` should be defined starting with the most specific rule and transitioning to the least specific rule.

```YAML
PublicRouteTable:
        Type: AWS::EC2::RouteTable
        Properties: 
            VpcId: !Ref VPC
            Tags: 
                - Key: Name 
                  Value: !Sub ${EnvironmentName} Public Routes

    DefaultPublicRoute: 
        Type: AWS::EC2::Route
        DependsOn: InternetGatewayAttachment
        Properties: 
            RouteTableId: !Ref PublicRouteTable
            DestinationCidrBlock: 0.0.0.0/0
            GatewayId: !Ref InternetGateway

    PublicSubnet1RouteTableAssociation:
        Type: AWS::EC2::SubnetRouteTableAssociation
        Properties:
            RouteTableId: !Ref PublicRouteTable
            SubnetId: !Ref PublicSubnet1

    PublicSubnet2RouteTableAssociation:
        Type: AWS::EC2::SubnetRouteTableAssociation
        Properties:
            RouteTableId: !Ref PublicRouteTable
            SubnetId: !Ref PublicSubnet2


    PrivateRouteTable1:
        Type: AWS::EC2::RouteTable
        Properties: 
            VpcId: !Ref VPC
            Tags: 
                - Key: Name 
                  Value: !Sub ${EnvironmentName} Private Routes (AZ1)

    DefaultPrivateRoute1:
        Type: AWS::EC2::Route
        Properties:
            RouteTableId: !Ref PrivateRouteTable1
            DestinationCidrBlock: 0.0.0.0/0
            NatGatewayId: !Ref NatGateway1

    PrivateSubnet1RouteTableAssociation:
        Type: AWS::EC2::SubnetRouteTableAssociation
        Properties:
            RouteTableId: !Ref PrivateRouteTable1
            SubnetId: !Ref PrivateSubnet1

    PrivateRouteTable2:
        Type: AWS::EC2::RouteTable
        Properties: 
            VpcId: !Ref VPC
            Tags: 
                - Key: Name 
                  Value: !Sub ${EnvironmentName} Private Routes (AZ2)

    DefaultPrivateRoute2:
        Type: AWS::EC2::Route
        Properties:
            RouteTableId: !Ref PrivateRouteTable2
            DestinationCidrBlock: 0.0.0.0/0
            NatGatewayId: !Ref NatGateway2

    PrivateSubnet2RouteTableAssociation:
        Type: AWS::EC2::SubnetRouteTableAssociation
        Properties:
            RouteTableId: !Ref PrivateRouteTable2
            SubnetId: !Ref PrivateSubnet2
```
##### #### Resources
  - [Route Tables Overview](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html)
  - [Route Table Documentation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-route-table.html)
  - [Route Documentation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-route.html)
  - [Subnet Route Table Association Documentation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-subnet-route-table-assoc.html)
## #### Outputs
`Outputs` are optional but are very useful if there are output values you need to:
  - import into another stack
  - return in a response
  - view in AWS console
  - To declare an Output use the following syntax:
```YAML
Outputs:
  Logical ID:
    Description: Information about the value
    Value: Value to return
    Export:
      Name: Value to export
```
The `Value` is required but the `Name` is optional. In the following example we are returning the id of our `VPC` as well as our Environment's Name:
```YAML
VPC: 
        Description: A reference to the created VPC
        Value: !Ref VPC
        Export:
          Name: !Sub ${EnvironmentName}-VPCID
```

## #### Join Function
You can use the `join` function to combine a group of `values`. The syntax requires you provide a delimiter and a list of values you want appended.

`Join` function syntax
`Fn::Join: [ delimiter, [ comma-delimited list of values ] ]`

In the following example we are using `!Join` to combine our subnets before returning their values:
```YAML
PublicSubnets:
        Description: A list of the public subnets
        Value: !Join [ ",", [ !Ref PublicSubnet1, !Ref PublicSubnet2 ]]
        Export:
          Name: !Sub ${EnvironmentName}-PUB-NETS
```
##### #### Resources
  - [Outputs Documentation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/outputs-section-structure.html)
  - [Join Function](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-join.html)
  - [Substitutes](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-sub.html)


