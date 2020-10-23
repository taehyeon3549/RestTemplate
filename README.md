# RestTemplate
// 주의: Map 형태로 parameter를 보낼경우 형태가 맞지 않아 오류 발생 필히 JSON 형태로 만들어서 보낼것

RestTemplate restTemplate = new RestTemplate();

JsonObject jsonObject = new JsonObject();

jsonObject.addProperty("destPhone", kakaoParm.getDestPhone().toString());
jsonObject.addProperty("info", kakaoParm.getInfo().toString());
jsonObject.addProperty("msgBody", kakaoParm.getMsgBody().toString());
jsonObject.addProperty("sendPhone", kakaoParm.getSendPhone().toString());
jsonObject.addProperty("sender", kakaoParm.getSender().toString());
jsonObject.addProperty("templateCode", kakaoParm.getTemplateCode().toString());

HttpHeaders headers = new HttpHeaders();

headers.setContentType(MediaType.APPLICATION_JSON);

HttpEntity<Object> entity = new HttpEntity(jsonObject.toString(), headers);

String url = "http://192.168.1.135:12101/kac/kakao";

Map<String,String> response = restTemplate.postForObject(url, entity, Map.class);

log.info(response.toString());
