from selenium import webdriver
from selenium.webdriver.common.keys import Keys
import time
import requests
from bs4 import BeautifulSoup

url_mensajes_biblicos = 'https://www.subiblia.com/devocional-diario/'

respuesta = requests.get(url_mensajes_biblicos)

if respuesta.status_code == 200:
    contenido = respuesta.text
    soup = BeautifulSoup(contenido,'html.parser')
    msg = soup.find_all('p')
    msg = msg[1].text
else:
    print('La pagina web no esta accesible')


driver = webdriver.Chrome(executable_path='C:/Driver_Chrome/chromedriver.exe')

driver.get('https://web.whatsapp.com/')
driver.maximize_window()

nombre_destinatario = 'SaidSuperAutos'

msg = msg + '\nSaludos y Bendiciones'

input('\nEscanea el QR code y luego presiona cualquier tecla para continuar...\n')

#Ubicamos el campo donde escribiremos el nombre del contacto, escribimos el nombre y por ultimo damos enter
#para que nos presente la ventana de interaccion con este contacto (campo para escribir el mensaje y boton de enviar)
ubica_contacto = driver.find_element_by_xpath("//*[@id='side']/div[1]/div/label/div/div[2]") 
ubica_contacto.send_keys(nombre_destinatario)
ubica_contacto.send_keys(u'\ue007')

#Esta es otra forma de ubicar un contacto pero algunas veces falla por eso se usa la de arriba
# contacto = driver.find_element_by_xpath("//span[@title='{}']".format(nombre_destinatario))
# contacto.click()

#Ubicamos el campo donde se escribe el mensaje y luego escribimos nuestro mensaje
mensaje = driver.find_element_by_xpath("//*[@id='main']/footer/div[1]/div[2]/div/div[2]")
mensaje.send_keys(msg)

#Ubicamos el boton enviar y luego damos click para que se envie el mensaje
boton_enviar= driver.find_element_by_xpath("//*[@id='main']/footer/div[1]/div[3]/button")
boton_enviar.click()

print('Mensaje enviado exitosamente')

