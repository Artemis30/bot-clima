import os
import requests

# --- CONFIGURACIÓN DE SECRETOS (GITHUB ACTIONS) ---
WEATHER_API_KEY = os.getenv("WEATHER_API_KEY")
TELEGRAM_TOKEN = os.getenv("TELEGRAM_TOKEN")
CHAT_ID = os.getenv("CHAT_ID")
CIUDAD = os.getenv("CIUDAD")
CIUDAD2 = os.getenv("CIUDAD2")

def obtener_clima():
    # Verificamos que la ciudad no esté vacía
    if not CIUDAD:
        return "❌ Error: No se ha configurado la variable de ciudad (CIUDAD)."
    url = f"http://api.openweathermap.org/data/2.5/weather?q={CIUDAD}&appid={WEATHER_API_KEY}&units=metric&lang=es" 
    try:
        response = requests.get(url)
        datos = response.json()
        
        if response.status_code == 200:
            temp = datos['main']['temp']
            desc = datos['weather'][0]['description']
            
            mensaje = f"🌍 Clima en {CIUDAD}:\n"
            mensaje += f"🌡️ Temp: {temp}°C\n"
            mensaje += f"☁️ Info: {desc.capitalize()}\n"
            
            # Lógica de avisos
            if "lluvia" in desc.lower() or "llovizna" in desc.lower():
                mensaje += "\n⚠️ ¡Lleva paraguas! ☔"
            elif temp < 10:
                mensaje += "\n❄️ ¡Abrígate, hace frío! 🧥"
            else:
                mensaje += "\n😸 ¡Que tengas un buen dia!"
            return mensaje
        else:
            return f"❌ Error API Clima: {datos.get('message', 'Error desconocido')}"
    except Exception as e:
        return f"❌ Error de conexión: {e}"

def CIUDAD2_clima():
    if not CIUDAD2:
        return "❌ Error: No se ha configurado la variable de ciudad secundaria (CIUDAD2)."
    url = f"http://api.openweathermap.org/data/2.5/weather?q={CIUDAD2}&appid={WEATHER_API_KEY}&units=metric&lang=es"
    try:
        response = requests.get(url)
        datos = response.json()
        
        if response.status_code == 200:
            temp = datos['main']['temp']
            desc = datos['weather'][0]['description']
            
            mensaje = f"🌍 Clima en {CIUDAD2}:\n"
            mensaje += f"🌡️ Temp: {temp}°C\n"
            mensaje += f"☁️ Info: {desc.capitalize()}\n"
            
            # Lógica de avisos
            if "lluvia" in desc.lower() or "llovizna" in desc.lower():
                mensaje += "\n⚠️ ¡Lleva paraguas! ☔"
            elif temp < 10:
                mensaje += "\n❄️ ¡Abrígate, hace frío! 🧥"
            else:
                mensaje += "\n😸 ¡Que tengas un buen dia!"
            return mensaje
        else:
            return f"❌ Error API Clima: {datos.get('message', 'Error desconocido')}"
    except Exception as e:
        return f"❌ Error de conexión: {e}"

def enviar_telegram(mensaje):
    url = f"https://api.telegram.org/bot{TELEGRAM_TOKEN}/sendMessage"
    payload = {"chat_id": CHAT_ID, "text": mensaje}
    requests.post(url, data=payload)

if __name__ == "__main__":
    informe = obtener_clima()
    enviar_telegram(informe)
    informe2 = CIUDAD2_clima()
    enviar_telegram(informe2)
    print(f"Proceso completado para la ciudad: {CIUDAD}")
    
