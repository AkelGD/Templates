import discord
import platform
import socket

TOKEN = 'BOT_TOKEN'
CHANNEL_ID = 123456789012345678 # Your channel ID

client = discord.Client()

@client.event
async def on_ready():
    print(f'Logged in as {client.user}')
    channel = client.get_channel(CHANNEL_ID)
    if channel:
        os_info = gather_os_info()
        await channel.send(os_info)
    else:
        print(f'Channel with ID {CHANNEL_ID} not found.')

def gather_os_info():
    ip_address = get_ip_address()
    os_info = (
        f"**Operating System Information**\n"
        f"- **System**: {platform.system()}\n"
        f"- **Release**: {platform.release()}\n"
        f"- **Version**: {platform.version()}\n"
        f"- **Machine**: {platform.machine()}\n"
        f"- **Processor**: {platform.processor()}\n"
        f"- **IP Address**: {ip_address}\n"
    )
    return os_info

def get_ip_address():
    try:
        
        s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
        
        s.connect(('8.8.8.8', 80))
        ip_address = s.getsockname()[0]
    except Exception as e:
        ip_address = f'Unable to determine IP address: {e}'
    finally:
        s.close()
    return ip_address

client.run(TOKEN)
