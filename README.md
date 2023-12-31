## AWS CLI の基本

1. AWS CLI のバージョンを表示し、使用できることを確認します。

  ```
  aws --version
  ```

1. AWS CLI を使用して Amazon EC2 インスタンスの情報を表示する権限をもっているか確認します。

  ```
  aws ec2 --dry-run describe-instances 
  ```

1. AWS CLI を使用して Amazon EC2 インスタンスの情報を表示します。 

  ```
  aws ec2 describe-instances 
  ```
   - 多くの情報が表示されることを確認します。
   - 確認後、ターミナルにプロンプトが戻らない場合は `q` キーを押下して下さい。
     
1. AWS CLI の `query` オプションを使用して Amazon EC2 インスタンスの情報の一部だけを表示します。 
   - 次の例ではインスタンス ID だけを表示しています。
  ```
  aws ec2 describe-instances  --query "Reservations[*].Instances[*].[InstanceId]" 
  ```

1. AWS CLI の `query` オプションを使用して Amazon EC2 インスタンスの情報の一部だけを表示します。 
   - 次の例ではインスタンス ID と インスタンスタイプを表示しています。
  ```
  aws ec2 describe-instances  --query "Reservations[*].Instances[*].[InstanceId,InstanceType]" 
  ```

1. AWS CLI の `instance-id` オプションと `output` オプションを使用して 特定の Amazon EC2 インスタンスのインスタンスタイプの表示形式を指定しています。 
   - 次の例では出力形式をテキストに指定しています。他にも `yaml` や `table` も指定できます。 **i-xxx** の部分は実際のインスタンス ID に置換えて下さい。
  ```
  aws ec2 describe-instances  --instance-id i-xxx --query "Reservations[*].Instances[*].InstanceType" --output text
  ```

1. AWS CLI の実行結果を環境変数に入れる場合などは、`--output text` の場合が役立ちます。
   - 下記は Linux の bash での実行例です。**i-xxx** の部分は実際のインスタンス ID に置換えて下さい。
  ```
  INSTANCE_TYPE=$(aws ec2 describe-instances  --instance-id i-xxx --query "Reservations[*].Instances[*].InstanceType" --output text)
  echo ${INSTANCE_TYPE}
  ```

 

