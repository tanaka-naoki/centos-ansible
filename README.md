# LAMP 環境用 centOS6.5

## ansible フォルダ構成

	localhost_lamp/
	  group_vars/
	    group1              特定のグループの変数を、ここで代入
	  host_vars/
	    hostname1           システムに特定の変数が必要な場合は、ここに置く
	  roles/                localhost_lamp用roles
	  site.yml              マスターplaybook

	roles/                   共通のroles
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
	vars/                   共通変数

## ansible コマンド

+ ローカル実行時  
ansible-playbook site.yml --connection=local


+ 疎通確認など  
ansible -i hosts web1 -m ping  


+ playbook実行  
ansible-playbook -i hosts site.yml


+ playbook文法確認  
ansible-playbook -i hosts site.yml --syntax-check


+ playbook ドライラン  
ansible-playbook -i hosts site.yml --check