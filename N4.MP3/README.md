# Wear OS Audio Assistance App - Projeto DOMA

Este projeto representa um aplicativo concebido pela empresa DOMA destinado a dispositivos Wear OS, com o propósito de prover auxílio a indivíduos com deficiência visual. O aplicativo monitora as notificações do dispositivo, transformando-as em áudio e proporcionando uma experiência de utilização acessível e inclusiva.

## Funcionalidades

### AudioHelper

A classe `AudioHelper` disponibiliza métodos para verificar a disponibilidade de saída de áudio e registrar callbacks para detectar dispositivos de áudio adicionados ou removidos. Principais funções:

- `audioOutputAvailable(int type)`: Avalia a presença da saída de áudio especificada no dispositivo.
- `registerAudioDeviceCallback()`: Inscreve um callback para detectar dispositivos de áudio adicionados ou removidos.

### TexttoSpeech

A classe `TexttoSpeech` é encarregada de fornecer funcionalidades para a conversão de texto em fala (Text-to-Speech, TTS). Principais funções:

- `speak(String text)`: Transforma o texto especificado em áudio e reproduz em voz alta.
- `shutdown()`: Interrompe a reprodução de áudio e libera recursos do TextToSpeech.

### NotificationService

O serviço `NotificationService` amplia a classe `NotificationListenerService` e tem a responsabilidade de monitorar as notificações do dispositivo. Principais funções:

- `onNotificationPosted(StatusBarNotification sbn)`: É acionado quando uma nova notificação é postada. Transforma o texto da notificação em áudio e reproduz em voz alta.
- `onNotificationRemoved(StatusBarNotification sbn)`: É acionado quando uma notificação é removida.

### MainActivity

A `MainActivity` é a atividade principal do aplicativo, onde a interface do usuário é apresentada e as funcionalidades são utilizadas. Principais funcionalidades:

- Inicializa o serviço de escuta de notificações (`NotificationService`).
- Avalia a disponibilidade de saída de áudio e atualiza a interface do usuário conforme necessário.
- Oferece um botão para acessar as configurações Bluetooth.
- Utiliza o `TexttoSpeech` para comunicar mensagens ao usuário.

## Instruções de Uso

1. Efetue a instalação do aplicativo no seu dispositivo Wear OS.
2. Conceda as permissões necessárias, especialmente a autorização para acessar as notificações do dispositivo.
3. Ao receber notificações, o aplicativo as converterá em áudio e as reproduzirá em voz alta para o usuário.

## Contribuições

Contribuições para o desenvolvimento e aprimoramento do aplicativo são bem-vindas. Sinta-se à vontade para enviar pull requests ou relatar problemas no repositório do projeto.

```kotlin
// Exemplo de uso do AudioHelper
val audioHelper = AudioHelper(context) // Substitua 'context' pelo contexto atual do seu aplicativo

val isSpeakerAvailable = audioHelper.audioOutputAvailable(AudioDeviceInfo.TYPE_BUILTIN_SPEAKER)
// Verdadeiro se o dispositivo tiver um alto-falante

val isBluetoothHeadsetConnected =
    audioHelper.audioOutputAvailable(AudioDeviceInfo.TYPE_BLUETOOTH_A2DP)
// Verdadeiro se um fone de ouvido Bluetooth estiver conectado
```
