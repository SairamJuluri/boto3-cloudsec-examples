import boto3

s3 = boto3.client('s3')
buckets = s3.list_buckets()['Buckets']

for bucket in buckets:
    name = bucket['Name']
    try:
        acl = s3.get_bucket_acl(Bucket=name)
        for grant in acl['Grants']:
            if 'AllUsers' in str(grant['Grantee']):
                print(f"Public Bucket: {name}")
    except Exception as e:
        print(f"Couldn't check {name}: {e}")
