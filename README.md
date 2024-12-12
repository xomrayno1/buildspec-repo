#local build support <br>

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
    
