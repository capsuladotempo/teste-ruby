# Desafio para desenvolvedores Ruby.

O objetivo desse teste é conhecer um pouco mais do seu conhecimento do Ruby, sua lógica, organização do código e responsabilidades. É baseada em uma implementação de um processamento simples, o qual é descrito a baixo.

## Case
A Capsula do Tempo está estruturando melhor seus sistemas, principalmente as APIs que recebem todo o conteúdo coletado nos eventos que estamos presentes. Nosso objetivo principal é melhorar a nossa performance para suporta a expansão que já está acontecendo!

Para que os sistemas continuem responsivos o tempo de respostas das APIs é um dos pontos mais importantes, bem como a confiabilidade de cada endpoint.

Um dos nossos principais endpoints tem a responsabilidade de fazer o recebimento e tratamento do payload para que possamos na sequência fazer a persistência e processamento das capsulas do tempo para que posteriormente nós façamos o envido para os destinatários. 

## Informações Complementares

O `JSON` a seguir exemplifica um payload fictícios de uma capsula capturada por uma das nossas máquinas.

  - Utilize o Ruby em conjunto com o framework / gem que desejar para implementar o desafio;
  - Implemente o parse do **Payload** abaixo;
  - Envie o resultado do processamento para (https://capsuladotempo.com/), no formato descrito no item **Processamento** (não considere o retorno da requisição, é apenas uma simulação);
  - Enviar com o Header 'X-MACHINE-TIME' com a data/hora atual no formato: 10:10:10 - 06/10/21 (dia/mê/ano);
  - Persistir os dados da capsula no banco de dados;
  - Disponibilizar o código em algum repositório público (github,  bitbucket, etc...);
  - :warning: Testes ganham uns pontos extras;
  - Enviar o link do repositório para **contato@capsuladotempoeventos.com.br**.

## Payload
```json
{
  "id": 1,
  "machine_id": 1,
  "recorded_at": "2019-06-24T16:45:32.000-04:00",
  "video_sequence": 39,
  "file_compression": "h264",
  "file_type": "mov",
  "file_name": "2839.mov",
  "video_length": 1109,
  "status": "syncing",
  "event": {
    "id": 1,
    "event_name": "Patrick Brithday",
    "event_date": "2021-10-10",
    "contact_name": "Andrei"
  }
}
```

## Processamento

Abaixo mais detalhes do payload esperado na API, resultado do processamento dos dados informados no payload acima.

  - **Todos os campos são obrigatórios**

```JSON
{
  "id": 1,
  "recorded_at": "2019-06-24T16:45:32.000-04:00",
  "status": "syncing",
  "machine": {
    "id": 1
  },
  "event": {
    "id": 1,
    "event_name": "Patrick Brithday",
    "event_date": "2021-10-10",
    "contact_name": "Andrei"
  },
  "file": {
    "position": 39,
    "compression": "h264",
    "type": "mov",
    "name": "2839.mov",
    "length": 1109,
  },
  "machine": {
      "id": 1
  }
}
```
