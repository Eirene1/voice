compile 'com.nexmo:client:4.+'

NexmoClient client = NexmoClient.builder()
  .applicationId("APPLICATION_ID")
  .privateKeyPath("PATH_TO_PRIVATE_KEY")
  .build();

Ncco ncco = new Ncco(
  TalkAction
    .builder("This is a text to speech call from Nexmo")
    .voiceName(VoiceName.SALLI)
    .build()
);


String TO_NUMBER = "";
String FROM_NUMBER = "";

CallEvent result = client
  .getVoiceClient()
  .createCall(new Call(TO_NUMBER, FROM_NUMBER, ncco));

System.out.println(result.getConversationUuid());
