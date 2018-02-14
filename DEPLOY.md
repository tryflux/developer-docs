bundle exec middleman build --clean
cd build
aws s3 sync . s3://<bucket>
