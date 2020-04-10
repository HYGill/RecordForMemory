# AWS API Gateway, Lambda, S3

***
해야할일

1.  IAM 보안자격증명 생성
2. Lambda 함수 생성
3. API Gateway와 Lambda 연결
4. S3 버킷 생성
5. 코드 작성

- 원래 계획은 별도의 IDE를 이용하여 Lambda함수에 업로드 할 계획이었으나 Docker를 깔아야하는 등 많은 설치와 설정이 필요해서 인라인 코드로 실습을 대체
[하고 싶은 사람은 참고]([https://aws.amazon.com/ko/blogs/korea/aws-toolkit-for-intellij-now-generally-available/](https://aws.amazon.com/ko/blogs/korea/aws-toolkit-for-intellij-now-generally-available/)
***

## Lambda 함수 생성
1. 트리거 추가
2. S3권한 설정

## API Gateway와 Lambda 연결
연결한 후 기본 Test 진행 하는 것 보여주기

## S3 버킷 생성
CORS 구성 추가

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<CORSConfiguration xmlns="http://s3.amazonaws.com/doc/2006-03-01/">
<CORSRule>
    <AllowedOrigin>*</AllowedOrigin>
    <AllowedMethod>GET</AllowedMethod>
    <MaxAgeSeconds>3000</MaxAgeSeconds>
    <AllowedHeader>Authorization</AllowedHeader>
</CORSRule>
<CORSRule>
    <AllowedOrigin>*</AllowedOrigin>
    <AllowedMethod>POST</AllowedMethod>
    <MaxAgeSeconds>3000</MaxAgeSeconds>
    <AllowedHeader>Authorization</AllowedHeader>
</CORSRule>
</CORSConfiguration>
```

## 코드 작성


``` nodejs
const AWS = require('aws-sdk');

const IAM_USER_KEY = '';
const IAM_USER_SECRET = '';

exports.handler = async (event) => {
	let s3bucket = new AWS.S3({
				accessKeyId: IAM_USER_KEY,
				secretAccessKey: IAM_USER_SECRET,
				Bucket: "gilluploads3"
	});
	
	try {
        const destparams = {
            Bucket: "gilluploads3",
			Key: "d.txt",
			Body: event.body
        };

        await s3bucket.putObject(destparams).promise();
        
        const response = {
        	body: JSON.stringify('upload Success')
    	};
    	
		return response;
    	
    } catch (error) {
        console.log(error);
        return error;
    }
};
```

## 결과
- txt파일이 s3에 업로드 된다.
- 사진 파일을 실습으로 하려고 했으나 nodeJS상의 별도의 모듈이 필요해 인라인 코드로는 한계가 있음을 느끼고 그냥 간단하게 txt파일로 진행
