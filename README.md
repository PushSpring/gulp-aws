gulp-aws
=========

AWS CLI plugin for [gulp](https://github.com/wearefractal/gulp).


# Install

```
npm install gulp-aws --save-dev
```


# Features

- Upload to S3



# API

### aws.s3(options)

Upload files to AWS S3.

#### Required options

- `aws_region`: AWS region
- `aws_key`: AWS access key
- `aws_secret`: AWS access secret

#### Other options

- `aws_cli_path`: The path of the AWS CLI. Defaults to `/usr/local/bin/aws`

#### Example

Create a tar.gz with the content of the 'src' directory and upload it to S3

```
var aws  = require('gulp-aws');
var tar  = require('gulp-tar');
var gzip = require('gulp-gzip');

gulp.task('my-task', function() {
    return gulp.src('src/**/*')
        .pipe(tar('mypackage.tar'))
        .pipe(gzip())
        .pipe(gulp.dest('./build'))
        .pipe(aws.s3('my-bucket-name', 'mypackage.tar.gz', {
            aws_region: 'eu-west-1',
            aws_key:    'your aws key kere',
            aws_secret: 'your aws secret here'
        }));
});
```
