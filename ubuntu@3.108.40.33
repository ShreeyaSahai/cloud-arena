from fastapi import FastAPI
import time
import random

app = FastAPI()

@app.get("/health")
def health():
    return {"status": "ok", "server": "cloudarena-1"}

@app.get("/game/join")
def join_game(player_id: str = "player_1", region: str = "ap-south-1"):
    # Simulate processing time (like a real game server would)
    latency = random.uniform(10, 50)
    time.sleep(latency / 1000)
    
    return {
        "player_id": player_id,
        "region": region,
        "server_latency_ms": round(latency, 2),
        "status": "joined",
        "timestamp": time.time()
    }

@app.get("/game/status")
def server_status():
    return {
        "active_players": random.randint(50, 500),
        "server_load": random.uniform(20, 90),
        "region": "ap-south-1"
    }
    