# RestTemplate
// 주의: Map 형태로 parameter를 보낼경우 형태가 맞지 않아 오류 발생 필히 JSON 형태로 만들어서 보낼것

RestTemplate restTemplate = new RestTemplate();

JsonObject jsonObject = new JsonObject();

jsonObject.addProperty("sittnId", kakaoParm.getSittnId().toString());

Map<String,String> parameters = new HashMap<>();
parameters.put("sittnId", String.valueOf(kakaoParm.getSittnId()));


HttpHeaders headers = new HttpHeaders();

headers.setContentType(MediaType.APPLICATION_JSON);

HttpEntity<String> entity = new HttpEntity<String>(jsonObject.toString(), headers);			
  
String url = "http://localhost:12100/kac/sittn";									

Map<String,String> response = restTemplate.postForObject(url, entity, Map.class);

