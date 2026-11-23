1. [Get current IAM identity](https://docs.aws.amazon.com/cli/latest/reference/sts/get-caller-identity.html)
    ```
    aws sts get-caller-identity
    ```
2. [Create key pair](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/create-key-pairs.html#having-ec2-create-your-key-pair)
    ```
     aws ec2  create-key-pair --key-name devops-kp --key-type rsa
     ```