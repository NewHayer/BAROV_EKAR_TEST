# BAROV_EKAR_TEST
FOR VOICE
import asyncio 
from concurrent.futures import ThreadPoolExecutor
import time
import requests
 
executor = ThreadPoolExecutor(max_workers=5)
loop = asyncio.get_event_loop()
 
async def make_requests():
    futures = [loop.run_in_executor(executor, requests.get, "https://www.apptic.me") for _ in range(5)]
    await asyncio.wait(futures)
 
start = time.time()
loop.run_until_complete(make_requests())
print(time.time() - start)
