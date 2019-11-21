# �@ myapp�����[�U�[�����ɉ𓀂��܂�
![image-20191119101214129.png](/knowledge/open.file/download?fileNo=51)
<br><br>
# �A �z�u����myapp�t�H���_�Ɉړ����܂�
```
cd C:\Users\myapp
```
<br><br>
# �B 
```
docker-compose run web rails new . --force --no-deps --database=mysql
```
�����s�����myapp�͈ȉ��Ƀt�@�C���������܂�
#### (1)Pulling db �imysql�j
�@�@��mysql��DB���\�z
#### (2)Pulling from library/ruby
�@�@��ruby�̊����\�z
���uBundle complete!�v���o���犮���I
<br><br>
# �C DB�̐ݒ��ύX���邽�߁A��x�R���e�i���~���܂�
```
docker-compose down
```
<br><br>
# �D DB�̌�����ύX���܂�
C:\Users\myapp\config\database.yml�@��z�z�����t�@�C���Ńt�@�C�����Ə㏑�����܂�
<br><br>
# �E �t�@�C����z�u���܂�
C:\Users\myapp\mysql-confd�@�Ɂ@�t�@�C���idefault_authentication.cnf�j��z�u���܂�
<br><br>
# �F �R���e�i���r���h���܂�
```
docker-compose build
```
���uSuccessfully built �������������������v���o���犮���I
<br><br>
# �G ���DB���N�����܂�
```
docker-compose up -d db
```
<br><br>
# �H web���N�����܂�
```
docker-compose run web rake db:create
```
<br><br>
# �I up�@���܂� 
```
docker-compose up -d
```
<br><br>
![image-20191120110345036.png](/knowledge/open.file/download?fileNo=54)
<br>
# ���`�F�b�N�|�C���g��
����ɋN�����Ă��邩���m�F
```
docker ps -a
```
![image-20191120105738281.png](/knowledge/open.file/download?fileNo=52)
���̂悤�Ɂumyapp_web�v�Ɓumysql�v�̃R���e�i��up���Ă����OK�I
<br>
![image-20191120110345036.png](/knowledge/open.file/download?fileNo=54)
<br><br>
# �J bash�ő��삷�邽�߂ɁA�R���e�i�փ��O�C��
```
docker exec -it CONTAINER_ID bash
```
��`CONTAINER_ID`�́A�S���ʂ�ID���U���Ă��܂��B
![image-20191120105929084.png](/knowledge/open.file/download?fileNo=53)

<br><br>
# �K �ȉ����A�P�s�����s
```
rails g model Task title:string context:string level:integer
```
```
rails db:migrate
```
```
rails g controller Tasks
```
<br><br>
# �L myapp\app\controllers�@�z���̈ȉ��̃t�@�C����ҏW����
�Ώۃt�@�C���F
```

```
<br><br>
# �M myapp\db�@�z���̈ȉ��̃t�@�C����ҏW����
�Ώۃt�@�C���Fseeds.rb
```

```
<br><br>
# �N DB�Ƀf�[�^�𑗂�
```
rails db:seed
```
<br><br>
# �O myapp\config�@�z���̈ȉ��̃t�@�C����ҏW����
�Ώۃt�@�C���Froutes.rb
```

```
<br><br>
# �P �ȉ����A�P�s�����s
```
touch app/views/tasks/index.html.erb
```
```
touch app/views/tasks/show.html.erb
```
```
touch app/views/tasks/new.html.erb
```
```
touch app/views/tasks/edit.html.erb
```
<br><br>
# �Q �@�z���̈ȉ��̃t�@�C����ҏW����
�Ώۃt�@�C���Findex.html.erb
```

```
<br><br>
# �R �ȉ��ɐڑ����Ċm�F�I
```
http://localhost:3000/
```
![image-20191121003744232.png](/knowledge/open.file/download?fileNo=56)
<br>
���̂悤�ȉ�ʂ��\�����ꂽ�犮���I