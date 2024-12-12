#local build support

test file buildspec.yml ở local xem có chạy được không

#1: docker pull public.ecr.aws/codebuild/amazonlinux2-x86_64-standard:3.0
#2: docker pull public.ecr.aws/codebuild/local-builds:latest
#3 download script code build để run local build
   curl -O https://raw.githubusercontent.com/aws/aws-codebuild-docker-images/master/local_builds/codebuild_build.sh
#4: ./codebuild_build.sh -i public.ecr.aws/codebuild/amazonlinux2-x86_64-standard:3.0 -a .    <br>
  ./codebuild_build.sh : parameter đầu tiên là file script ở #3 tải về, 
  -i public.ecr.aws/codebuild/amazonlinux2-x86_64-standard:3.0: chỉ định docker image này cung cấp một môi trường build chuẩn
  -a . : chỉ định thư mục đầu ra sẽ lưu ở thư mục hiện tại

#5: nếu run thành công sẽ ra file artifacts.zip ở thư mục hiện tại
    
