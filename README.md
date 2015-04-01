# LAMP 環境用 centOS6.5

## ansible フォルダ構成

	group_vars/
	   group1              特定のグループの変数を、ここで代入
	host_vars/
	   hostname1           システムに特定の変数が必要な場合は、ここに置く

	site.yml               マスターplaybook
	web_servers.yml        webserver層のplaybook
	db_servers.yml         dbserver層のplaybook

	roles/
	  common/                この階層は "role" を表す
	    tasks/            
	        main.yml        <-- タスクファイルは正当であればより小さなファイルをインクルードできる
	    handlers/         
	        main.yml        <-- ハンドラファイル
	    templates/          <-- テンプレートで使用するファイル
	        ntp.conf.j2     <------- テンプレートファイル名は .j2 で終わる
	    files/            
	        bar.txt         <-- copy リソースで使用するファイル
	        foo.sh          <-- script リソースで使用するスクリプト
	hotfix                  緊急用playbook置き場
	library                 anasible自作モジュール
	
## ansible サーバ構成

+ 踏み台サーバ  31022
+ ver. ansible 1.9
+ デフォルトhostsは、/etc/ansible/hosts


## ansible コマンド

+ ローカル実行時  
ansible-playbook playbook.yml  


+ 疎通確認など  
ansible -i hosts web1 -m ping  


+ playbook実行  
ansible-playbook -i hosts playbook.yml  


+ playbook文法確認  
ansible-playbook -i hosts playbook.yml --syntax-check  


+ playbook ドライラン  
ansible-playbook -i hosts playbook.yml --check  