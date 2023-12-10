## AWS CLI をさわってみよう

1. Cloud9 画面下部のターミナルで次のコマンドを実行して AWS CLI が使用できることを確認します。
   - Cloud9 には AWS CLI が組み込まれています。
  ```
  aws --version
  ```
   - 次のように AWS CLI のバージョンが表示されます。(バージョン番号が異なっても問題ありません。） 
  ```
  aws-cli/2.12.3 Python/3.11.4 Linux/4.14.314-238.539.amzn2.x86_64 exe/x86_64.amzn.2 prompt/off
  ```
2. AWS CLI を使用して Amazon EC2 インスタンスの情報を表示します。 

  ```
  aws ec2 describe-instances 
  ```
   - 多くの情報が表示されることを確認します。
   - 確認後、ターミナルにプロンプトが戻らない場合は `q` キーを押下して下さい。
     
3. AWS CLI の `query` オプションを使用して Amazon EC2 インスタンスの情報の一部だけを表示します。 
   - 次の例ではインスタンス ID だけを表示しています。
  ```
  aws ec2 describe-instances  --query 'Reservations[*].Instances[*].InstanceId' 
  ```

4. AWS CLI の `query` オプションを使用して Amazon EC2 インスタンスの情報の一部だけを表示します。 
   - 次の例ではインスタンス ID と インスタンスタイプを表示しています。
  ```
  aws ec2 describe-instances  --query 'Reservations[*].Instances[*].[InstanceId,InstanceType]' 
  ```

5. AWS CLI の `output` オプションを使用して Amazon EC2 インスタンスの情報の表示形式を指定します。 
   - 次の例では出力形式をテキストに指定しています。他にも `yaml` や `table` を試してみましょう。
  ```
  aws ec2 describe-instances  --query 'Reservations[*].Instances[*].InstanceId' --output text
  ```