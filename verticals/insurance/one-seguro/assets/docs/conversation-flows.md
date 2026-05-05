# Conversation Flows - One Seguro

## Table of Contents
- [Flow 1: Welcome & Intent Detection](#flow-1-welcome--intent-detection)
- [Flow 2: Voice Claims Report](#flow-2-voice-claims-report)
  - [Scenario: Car Accident](#scenario-car-accident)
- [Flow 3: Web Claims Report (XApp)](#flow-3-web-claims-report-xapp)
- [Flow 4: Schedule a Service](#flow-4-schedule-a-service)
- [Flow 5: Schedule a Service (XApps)](#flow-5-schedule-a-service-xapps)
- [Flow 6: Escalation to Human Agent](#flow-6-escalation-to-human-agent)
- [Version Information](#version-information)

## Flow 1: Welcome & Intent Detection

**Agent (PT):** "Bom dia, eu sou a Sara, assistente virtual da One Seguros. Como posso te ajudar hoje?"  
**Agent (ES):** "Buenos días, soy Sara, asistente virtual de One Seguros. ¿Cómo puedo ayudarte hoy?"

**User Options (PT):**
- "Quero abrir um sinistro"
- "Quero agendar um serviço"
- "Falar com um atendente"

**User Options (ES):**
- "Quiero reportar un siniestro"
- "Quiero programar un servicio."
- "Hablar con un agente"

---

## Flow 2: Voice Claims Report

### Scenario: Car Accident

**Agent (PT):** "Claro, posso te ajudar com isso. Você prefere registrar o sinistro por voz comigo agora ou quer que eu te envie o link para fazer pela página web, que é mais rápido e fácil?"  
**Agent (ES):** "Claro, puedo ayudarte con eso. ¿Prefieres registrar el siniestro por voz conmigo ahora o quieres que te envíe el enlace para hacerlo en la página web, que es más rápido y fácil?"

---

**User (PT):** "Por voz"  
**User (ES):** "Por voz"

---

**Agent (PT):** "Perfeito. Para seguir com o registro, preciso confirmar algumas informações. Pode me dizer qual foi o tipo de sinistro? Foi colisão, furto, roubo ou outro tipo de dano?"  
**Agent (ES):** "Perfecto. Para continuar con el registro, necesito confirmar algunos datos. ¿Puedes decirme cuál fue el tipo de siniestro? ¿Fue colisión, hurto, robo u otro tipo de daño?"

---

**User (PT):** "Bati o carro ontem à noite"  
**User (ES):** "Choqué el auto anoche"

---

**Agent (PT):** "Entendido. Pode me informar em que cidade ou local aconteceu a colisão?"  
**Agent (ES):** "Entendido. ¿Puedes indicarme en qué ciudad o lugar ocurrió la colisión?"

---

**User (PT):** "Foi em São Paulo"  
**User (ES):** "Fue en São Paulo"

---

**Agent (PT):** "Certo. Houve envolvimento de terceiros no acidente ou foi apenas o seu veículo?"  
**Agent (ES):** "De acuerdo. ¿Hubo participación de terceros en el accidente o solo fue tu vehículo?"

---

**User (PT):** "Apenas o meu veículo"  
**User (ES):** "Solo mi vehículo"

---

**Agent (PT):** "Compreendido. As autoridades, como polícia ou guarda municipal, chegaram a ser acionadas no local?"  
**Agent (ES):** "Comprendido. ¿Las autoridades, como la policía o guardia municipal, fueron llamadas al lugar?"

---

**User (PT):** "Não precisaram ser acionadas"  
**User (ES):** "No fue necesario llamarlas"

---

**Agent (PT):** "Perfeito, obrigado pelas informações. Agora, só para confirmar: o sinistro foi uma colisão com seu veículo em São Paulo, ocorrido ontem à noite, sem envolvimento de terceiros e sem acionamento das autoridades, correto?"  
**Agent (ES):** "Perfecto, gracias por la información. Ahora, para confirmar: el siniestro fue una colisión con tu vehículo en São Paulo, ocurrido anoche, sin participación de terceros y sin intervención de autoridades, ¿correcto?"

---

**User (PT):** "Sim, está correto"  
**User (ES):** "Sí, es correcto"

---

**Agent (PT):** "Ótimo, vou registrar o sinistro para você. Pode me confirmar o modelo do seu veículo, por favor?"  
**Agent (ES):** "Perfecto, voy a registrar el siniestro. ¿Puedes confirmarme el modelo de tu vehículo, por favor?"

---

**User (PT):** "Corolla"  
**User (ES):** "Corolla"

---

**Agent (PT):** "Perfeito. E só para finalizar, lembra a data exata do sinistro? Foi no dia quatro de maio de dois mil e vinte e seis, correto?"  
**Agent (ES):** "Perfecto. Para finalizar, ¿recuerdas la fecha exacta del siniestro? ¿Fue el cuatro de mayo de dos mil veintiséis, correcto?"

---

**User (PT):** "Sim"  
**User (ES):** "Sí"

---

**Agent (PT):**
"Perfeito, estou registrando o sinistro do seu veículo Corolla, ocorrido em quatro de maio de dois mil e vinte e seis, em São Paulo, por colisão.

Seu sinistro foi registrado com sucesso. Em breve, você receberá o número de protocolo e as orientações sobre os próximos passos no seu contato cadastrado. Te ajudo em algo mais?"

**Agent (ES):**
"Perfecto, estoy registrando el siniestro de tu vehículo Corolla, ocurrido el cuatro de mayo de dos mil veintiséis, en São Paulo, por colisión.

Tu siniestro ha sido registrado con éxito. En breve recibirás el número de protocolo y las instrucciones sobre los próximos pasos en tu contacto registrado. ¿Puedo ayudarte en algo más?"

---

## Flow 3: Web Claims Report (XApp)

**Agent (PT):** "Claro, posso te ajudar com isso. Você prefere registrar o sinistro por voz comigo agora ou quer que eu te envie o link para fazer pela página web, que é mais rápido e fácil?"  
**Agent (ES):** "Claro, puedo ayudarte con eso. ¿Prefieres registrar el siniestro por voz conmigo ahora o quieres que te envíe el enlace para hacerlo en la página web, que es más rápido y fácil?"

---

**User (PT):** "Pela página web"  
**User (ES):** "Por la página web"

---

### Steps (PT / ES)

1. Seleção do tipo de sinistro / Selección del tipo de siniestro  
2. Detalhes do incidente / Detalles del incidente  
3. Localização / Ubicación  
4. Detalhes adicionais / Detalles adicionales  
5. Terceiros (se aplicável) / Terceros (si aplica)  
6. Upload de documentos / Carga de documentos  
7. Revisão e confirmação / Revisión y confirmación  

---

## Flow 4: Schedule a service

**Agent (PT):** "Olá, eu sou a Sara, assistente virtual da One Seguros. Como posso te ajudar hoje?"  
**Agent (ES):** "Hola, soy Sara, asistente virtual de One Seguros. ¿Cómo puedo ayudarte hoy?"

---

**User (PT):** "Quero agendar um serviço"  
**User (ES):** "Quiero agendar un servicio"

---

**Agent (PT):** "Claro, posso te ajudar com isso. Pode me informar qual tipo de serviço você deseja agendar? Por exemplo, chaveiro, eletricista, encanador ou assistência a eletrodomésticos."  
**Agent (ES):** "Claro, puedo ayudarte con eso. ¿Puedes indicarme qué tipo de servicio deseas agendar? Por ejemplo, cerrajero, electricista, plomero o asistencia de electrodomésticos."

---

**User (PT):** "Encanador"  
**User (ES):** "Plomero"

---

**Agent (PT):** "Perfeito. Para agendar o serviço de encanador, preciso apenas de duas informações: o número do seu documento e o código postal do local onde o serviço será realizado. Pode me passar esses dados, por favor?"  
**Agent (ES):** "Perfecto. Para agendar el servicio de plomería, solo necesito dos datos: tu número de documento y el código postal del lugar donde se realizará el servicio. ¿Puedes proporcionarlos, por favor?"

---

**User (PT):** "Documento de identificação é 12345 e código postal 123123"  
**User (ES):** "Mi documento es 12345 y el código postal es 123123"

---

**Agent (PT):** "Você prefere escolher uma data ou posso agendar para a data mais próxima disponível?"  
**Agent (ES):** "¿Prefieres elegir una fecha o puedo programarlo para la fecha más próxima disponible?"

---

**User (PT):** "Pode ser a mais próxima"  
**User (ES):** "La más próxima está bien"

---

**Agent (PT):** "A data mais próxima disponível é amanhã às nove da manhã."  
**Agent (ES):** "La fecha más próxima disponible es mañana a las nueve de la mañana."

---

**Agent (PT):**
"Seu serviço de encanador foi agendado para amanhã às nove da manhã no endereço com código postal 123123.

Muito obrigado. Posso te ajudar com mais alguma coisa?"

**Agent (ES):**
"Tu servicio de plomería ha sido agendado para mañana a las nueve de la mañana en la dirección con código postal 123123.

Muchas gracias. ¿Puedo ayudarte en algo más?"


## Flow 5: Schedule a service (XApps)

**Agent (PT):** "Olá, eu sou a Sara, assistente virtual da One Seguros. Como posso te ajudar hoje?"  
**Agent (ES):** "Hola, soy Sara, asistente virtual de One Seguros. ¿Cómo puedo ayudarte hoy?"

---

**User (PT):** "Quero agendar um serviço"  
**User (ES):** "Quiero agendar un servicio"

---

**Agent (PT):** "Claro, posso te ajudar com isso. Pode me informar qual tipo de serviço você deseja agendar? Por exemplo, chaveiro, eletricista, encanador ou assistência a eletrodomésticos."  
**Agent (ES):** "Claro, puedo ayudarte con eso. ¿Puedes indicarme qué tipo de servicio deseas agendar? Por ejemplo, cerrajero, electricista, plomero o asistencia de electrodomésticos."

---

**User (PT):** "Encanador"  
**User (ES):** "Plomero"

---

**Agent (PT):** "Perfeito. Para agendar o serviço de encanador, preciso apenas de duas informações: o número do seu documento e o código postal do local onde o serviço será realizado. Pode me passar esses dados, por favor?"  
**Agent (ES):** "Perfecto. Para agendar el servicio de plomería, solo necesito dos datos: tu número de documento y el código postal del lugar donde se realizará el servicio. ¿Puedes proporcionarlos, por favor?"

---

**User (PT):** "Documento de identificação é 12345 e código postal 123123"  
**User (ES):** "Mi documento es 12345 y el código postal es 123123"

---

**Agent (PT):** "Você prefere escolher uma data ou posso agendar para a data mais próxima disponível?"  
**Agent (ES):** "¿Prefieres elegir una fecha o puedo programarlo para la fecha más próxima disponible?"

**Agent (PT):** "Você prefere escolher uma data ou posso agendar para a data mais próxima disponível?"  
**Agent (ES):** "¿Prefieres elegir una fecha o puedo programarlo para la fecha más próxima disponible?"

---

**User (PT):** "Quero escolher"  
**User (ES):** "Quiero elegir"

---

**Agent (PT):** "Perfeito. Vou te enviar as opções de horários por mensagem para você escolher. Caso tenha alguma dúvida, é só me avisar."  
**Agent (ES):** "Perfecto. Te enviaré los horarios disponibles por mensaje para que puedas elegir. Si tienes alguna duda, no dudes en decírmelo."

---

### XApp: Scheduling Page

**Action:**
- Open XApp Page

**User Action:**
- Select Date, Time and confirm

---

### Confirmation

**Agent (PT):**
"Seu serviço de encanador foi agendado para o dia seis de maio de dois mil e vinte e seis às nove da manhã, no endereço informado.

Muito obrigado. Posso te ajudar com mais alguma coisa?"

**Agent (ES):**
"Tu servicio de plomería ha sido agendado para el seis de mayo de dos mil veintiséis a las nueve de la mañana en la dirección indicada.

Muchas gracias. ¿Puedo ayudarte en algo más?"


## Flow 6: Escalation to Human Agent

**User (PT):** "Preciso falar com um atendente"  
**User (ES):** "Necesito hablar con un agente"

---

**Agent (PT):** "Claro! Vou conectar você com um dos nossos especialistas. Só um momento..."  
**Agent (ES):** "Claro, voy a conectarte con uno de nuestros especialistas. Un momento por favor..."

---

**Human Agent (PT):** "Olá! Tudo bem? Vi que você está abrindo um sinistro de colisão. Como posso ajudar?"  
**Human Agent (ES):** "Hola, ¿todo bien? Vi que estás reportando un siniestro de colisión. ¿Cómo puedo ayudarte?"

## Version Information

**Last Updated:** May 4, 2025
**Version:** 1.0