from tarea123 import Preg

import requests

dato = Preg()

consulta_cat = dato.consultar({ })

pregunta = [ ]

categorias = [ ]

respuesta = [ ]

for i in consulta_cat:

    categorias.append(i["Categoria"])
   
    pregunta.append(i["Pregunta"])
   
    respuesta.append(i["Respuesta"])
   
categorias_filtradas = list(set(categorias))

print(categorias_filtradas)

for cat in categorias_filtradas:

    cat = str(cat)

    dats = dato.consultar ({"Categoria":str(cat)})


    for dat in dats:


      respuesta.append(dat["Respuesta"])

      pregunta.append( dat["Pregunta"] )

 filtro_preguntas = list(set(pregunta)), list(set(respuesta))
 
 print (filtro_preguntas)

    variable = {"contexts": [" "], "events": [], "fallbackIntent": False, "name": str(cat), "priority": 500000,    "responses": [{"action": "add.list", "affectedContexts": [{"lifespan": 5, "name": "" , "parameters": {}}], "defaultResponsePlatforms": {"google": True}, "messages": [{"platform": "google", "textToSpeech": ". ", "type": "simple_response"}, {"speech": str(respuesta), "type": 0}], "parameters": [ {"dataType": "0", "isList": True, "name": "0", "prompts": [" . "], "required": True, "value": "0"}], "resetContexts": False}], "templates": ["c:c ", "b:b ", "a:a "], "userSays": [{"count": 0, "data": [{"text": str(pregunta)}, {"userDefined": True}]}], "webhookForSlotFilling": False, "webhookUsed": False}
    query  = requests.post("https://api.dialogflow.com/v1/intents?v=20150910&lang=es",headers = {"Authorization": "Bearer 36de276d58914e07ac8af20fb5cc3652", "Content-Type": "application/json"},
    data=str(variable))
    print (query.text)
    
# allí le mando esa porqueria que tengo ahí, me disculpa por lo malo que hay y por subirlo mal ya que no se usar esto.
