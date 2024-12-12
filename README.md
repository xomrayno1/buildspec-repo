#xây dựng CodeBuild support <br>

test file buildspec.yml ở local xem có chạy được không  <br>

#1: docker pull public.ecr.aws/codebuild/amazonlinux2-x86_64-standard:3.0  <br>
#2: docker pull public.ecr.aws/codebuild/local-builds:latest  <br>
#3 download script code build để run local build  <br>
   curl -O https://raw.githubusercontent.com/aws/aws-codebuild-docker-images/master/local_builds/codebuild_build.sh  <br>
#4: ./codebuild_build.sh -i public.ecr.aws/codebuild/amazonlinux2-x86_64-standard:3.0 -a .    <br>
  ./codebuild_build.sh : parameter đầu tiên là file script ở #3 tải về,   <br>
  -i public.ecr.aws/codebuild/amazonlinux2-x86_64-standard:3.0: chỉ định docker image này cung cấp một môi trường build chuẩn  <br>
  -a . : chỉ định thư mục đầu ra sẽ lưu ở thư mục hiện tại  <br>

#5: nếu run thành công sẽ ra file artifacts.zip ở thư mục hiện tại  <br>

#Xây dựng CodeDeploy ở EC2 <br>
 - CodeDeploy agent chỉ cần ở EC2/on-prem instance deployment, ECS và Lambda deployment thì ko cần tải agent. <br>
 1. Login instance sử dụng terminal <br>
 2. sudo yum install wget -y <br>
 3.  wget https://aws-codedeploy-us-east-1.s3.amazonaws.com/latest/install <br>
 4.  Change the file permissions to execute using this command: <br>
    chmod +x ./install <br>
 5. Execute the CodeDeploy installer using the following command: <br> 
    sudo ./install auto <br>
 6. Once the CodeDeploy agent is installed on the instance, you can start it by running the following command: <br>
    service codedeploy-agent start <br>

For any Windows system installation, you can download the CodeDeploy agent msi installer using the following link: https://docs.aws.amazon.com/codedeploy/latest/userguide/ codedeploy-agent-operations-install-windows.html <br>

The CodeDeploy agent uses a configuration file called appsepc.yml to execute scripts on the EC2 instances using lifecycle events to perform the deployment. So, let’s explore the appspec.yml file in detail in the next section. <br>

    
