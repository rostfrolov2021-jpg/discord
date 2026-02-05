import discord
from discord.ext import commands

# Настраиваем доступы (Intents)
intents = discord.Intents.default()
intents.message_content = True  # Чтобы бот мог читать сообщения

# Создаем бота с префиксом "!" (команды будут начинаться с этого знака)
bot = commands.Bot(command_prefix='*', intents=intents)

# Событие: когда бот запустился
@bot.event
async def on_ready():
    print(f'Бот {bot.user} запущен и готов к работе!')

# Команда !привет
@bot.command()
async def привет(ctx):
    await ctx.send(f'Привет, {ctx.author.name}! Я твой бот на Python! 🤖')

# Команда !эхо (бот повторит твои слова)
@bot.command()
async def эхо(ctx, *, message):
    await ctx.send(message)

# Запуск бота (вставь сюда свой токен в кавычках)
bot.run('')
