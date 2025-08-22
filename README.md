from expert import EoApi as ExpertAPI
import time, random

expert = ExpertAPI(token="YOUR_TOKEN", server_region="wss://fr24g1eu.expertoption.com/")
expert.connect()
expert.SetDemo()
profile = expert.Profile()
print("Profile:", profile)

candles = expert.GetCandles()
print("Candles:", candles)

for _ in range(10):
    typ = random.choice(["call", "put"])
    expert.Buy(amount=10, type=typ, assetid=240, exptime=60, isdemo=1, strike_time=time.time())
    time.sleep(15)

