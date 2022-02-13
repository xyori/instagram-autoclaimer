
"""
2022/02/12
viper claimer using requests / hydra team
made by @y.ri
"""

from time import sleep
from random import choice
from threading import Thread

def stop():

   from signal import SIGTERM
   from os import kill, getpid
   return kill(getpid(), SIGTERM)

#clear = lambda: call( 'cls' , shell=True )

def importing():

   from subprocess import call
   from importlib import util
   module = "team hydra"
   pip = lambda: call( f'pip3 install {module}')
   What_ = util.find_spec("requests")
   if str(What_) == 'None':module="requests";pip()
   elif str(What_) != "None":pass
   What_ = util.find_spec("pyfiglet")
   if str(What_) == 'None':module="pyfiglet";pip()
   elif str(What_) != "None":pass
   What_ = util.find_spec("colorama")
   if str(What_) == 'None':module="colorama";pip()
   elif str(What_) != "None":pass
   What_ = util.find_spec("autopy")
   if str(What_) == 'None':module="autopy";pip()
   elif str(What_) != "None":pass
   del pip,module,What_
   call( 'cls' , shell=True )

importing()

from requests import post,get,Session
from autopy import alert

class C:

   from colorama import Fore,init,Style
   SR  =    Style.RESET_ALL
   SB  =       Style.BRIGHT
   SRB =        SR   +   SB
   FG  =    SB+  Fore.GREEN
   FC  =    SB+   Fore.CYAN
   FR  =     SB+   Fore.RED
   FY  =    SB+ Fore.YELLOW
   FB  =    SB+   Fore.BLUE

keep_alive = Session()
C.init(autoreset=True)

class j:
   
   from json import loads

   close_me_please = open("settings.txt","r")

   r = close_me_please.read()
   n_ = loads(r)["settings"]["name"]
   bi_ = loads(r)["settings"]["biography"]
   ni_ = loads(r)["settings"]["nickname"]
   b_ = loads(r)["settings"]["banner"]
   m_ = loads(r)["settings"]["message"]
   w_ = loads(r)["settings"]["webhook"]
   close_me_please.close()

def close():
   
   print(f'{C.SB}[{C.FR}!!{C.SRB}] press enter to terminate: ',end='')
   input();stop()

def max(items:list):

   maximum = 0
   for item in items:
      if item > maximum:
         maximum = item
   return maximum
   
def len(item):

   len = 0
   for _ in item:
      len += 1
   return len

def ksm_ghost():

   from pyfiglet import figlet_format
   from ctypes import windll

   title = [

      'Codded by hydra',
      'We will bury them',

            ]

   windll.kernel32.SetConsoleTitleW(f'[ {j.n_} ]')
   print(f'{C.SRB}     ( {C.FG}{choice(title)}{C.SRB} )\n{C.FG}{figlet_format(f" {j.b_}", font = "slant" )}')
   del title

ksm_ghost()

class System:

   def __init__(self):
      
      self.running = True
      self.threads = []
      self.claim_ = []
      self.attempts = 0
      self.ratelimit = 0
      self.claim_status = False
      self.proxy_error = 0
      self.request_per_second = 0

      sessions_file_close_me = open("sessions.txt",'r')
      self.sessions = sessions_file_close_me.read().splitlines()
      sessions_file_close_me.close

      proxies_file_close_me = open("proxies.txt",'r')
      self.proxies = proxies_file_close_me.read().splitlines()
      proxies_file_close_me.close

      print(f'\n\t{C.SB}[{C.FG}//{C.SRB}] enter target {C.FG}@: ',end='')
      self.target = str(input())
      print(f'\t{C.SB}[{C.FG}//{C.SRB}] enter threads {C.FG}?: ',end='')
      self.thread = int(input())
      print(f'\t{C.SB}[{C.FG}//{C.SRB}] enter loops {C.FG}?: ',end='')
      self.loop = int(input())

      print()
      self.thread_base()

   def request_counter_(self):

      while True:

         second_before = self.attempts
         sleep(1)
         self.request_per_second = self.attempts - second_before

   def send_discord(self):

        data = {}
        data["embeds"] = [{"description": f"\n** {j.m_} : @{self.target} **",
                           "color": choice([0x3498db, 0x2ecc71, 0xe91e63, 0xf1c40f, 0xe74c3c, 0xe67e22]),
                           "footer": {"text": f'total requests: {self.attempts} | requests/s: {max(self.claim_)}'},
                           "thumbnail": {"url": 'https://media.tenor.com/images/17a90373b4aa59444b62aa6845c4afdb/tenor.gif'}, "author": {"name": "viper/claimer"}}]
        try:
            post(j.w_, json=data)
        except Exception:pass
        
   def bio_name_changer_(self):

        try:
         post(
                  url='https://i.instagram.com/api/v1/accounts/set_phone_and_name/', 
                  headers={'User-Agent': 'Instagram 93.1.0.19.102 Android (21/5.0.2; 240dpi; 540x960; samsung; SM-G530H; fortuna3g; qcom; ar_AE; 154400379)',"Cookie": f"sessionid={self.session}"}, 
                  data={"first_name": j.ni_}
             )
         post(
                  url='https://i.instagram.com/api/v1/accounts/set_biography/',
                  headers={'User-Agent': 'Instagram 152.0.0.1.60 Android', "Cookie": f"sessionid={self.session}"},
                  data={f"raw_text": j.bi_}
             )
        except Exception:pass

   def email_(self):

      try:
         resp = str(get("https://i.instagram.com/api/v1/accounts/current_user/?edit=true",headers={"Accept": "*/*", "Accept-Encoding": "gzip, deflate","Accept-Language": "en-US","User-Agent": "Instagram 85.0.0.21.100 Android (28/9; 380dpi; 1080x2147; OnePlus; HWEVA; OnePlus6T; qcom; en_US; 146536611)","X-IG-Capabilities": "3brTvw==", "X-IG-Connection-Type": "WIFI"},cookies={"sessionid": self.session}).json())
         try:email = resp.split("'email':")[1].split("'")[1]
         except Exception:email='could not parse email'
         open(f'claims/@{self.target}.txt', 'a').write(f'\nsession: {self.session}\nemail: {email}\nnice.\n')
      except Exception:pass
   
   def profile_pic(self):
      
      try:
         resp = get(url="https://www.instagram.com").cookies
         crf = resp["csrftoken"]
         post(
            url="https://www.instagram.com/accounts/web_change_profile_picture/",
            headers={"user-agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.82 Safari/537.36","x-csrftoken":crf,"cookie":f"sessionid={self.session}"}
            )
      except Exception:pass

   def functions_mannger(self):

      from ctypes import windll
      slash = ['\\','|','/','-']
      while True:

         n = 0
         for _ in slash:

            if self.claim_status == False:

               windll.kernel32.SetConsoleTitleW(f"[{slash[n]}] REQ:{self.attempts} - RS:{self.request_per_second} - SID:{len(self.sessions)} - BLC:{self.ratelimit} - ER:{self.proxy_error}")
               sleep(0.4)
               n += 1

            elif self.claim_status == True:

               print(f'\n   {C.SB}{j.m_}{C.FG} @{self.target}')
               windll.kernel32.SetConsoleTitleW(f"[{self.target}] REQ:{self.attempts} - RS:{self.request_per_second} - SID:{len(self.sessions)} - BLC:{self.ratelimit} - ER:{self.proxy_error}")
               
               self.send_discord()
               self.email_()
               self.bio_name_changer_()
               self.profile_pic()

               alert.alert(f'claimed > {self.target}  \nattempts > {self.attempts:,}\nrequests/sec > {max(self.claim_)}','viper')
               stop()

   def request_(self):

      while self.running:

         session = choice(self.sessions)
         try:

            response = keep_alive.post(url="https://i.instagram.com/api/v1/accounts/set_username/",headers={'User-Agent': 'Instagram 93.1.0.19.102 Android (21/5.0.2; 240dpi; 540x960; samsung; SM-G530H; fortuna3g; qcom; ar_AE; 154400379)','Connection': 'close', 'Cookie': f'sessionid={session}'},data={'username': self.target},proxies={'http':f'{choice(self.proxies)}'}).text
            if '"status":"ok"' in response:
               self.claim_.append(self.request_per_second)
               self.session = session
               self.claim_status = True
               self.running = False
               break
            elif "This username isn't available." in response:self.attempts +=1
            elif "Please wait a few minutes before you try again." in response:self.ratelimit += 1
            elif "checkpoint_required" in response or "feedback_required" in response or "challenge_required" in response or "login_required" in response:
               try:self.sessions.remove(session)
               except ValueError:pass
               except IndexError:pass
         
         except Exception:
            self.proxy_error += 1
         
   def generating_threads(self):

      [
         [self.threads.append(
               Thread(target=self.request_, daemon=True))
            for _ in range(self.thread)]
         for _ in range(self.loop)
      ]

   def thread_base(self):

      self.generating_threads()

      Thread(target=self.request_counter_).start()
      Thread(target=self.functions_mannger).start()
      alert.alert(f'ready? start', 'viper')
      
      for threads_waiting in self.threads:
             threads_waiting.start()

if __name__ == "__main__":
   System()
