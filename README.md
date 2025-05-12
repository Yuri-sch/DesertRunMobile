# DesertRunMobile
Projeto desenvolvido para a disiplina "Desenvolvimento de Aplicações para Dispositivos Móveis", da Univates. Consiste em um simples projeto que exporta um projeto de um jogo em Unity como uma view para o Android Studio. Feito individualmente por mim - Yuri Ezequiel Schaffer
É um jogo de plataforma 2d em que o personagem anda automaticamente e precisa pular entre plataformas e coletar moedas. O jogo é infinito e tem uma pontuações.
Infelizmente, eu não consegui exportar todo o meu projeto, pois alguns arquivos ultrapassaram 2GB, limite que o github não aceita (se alguém que estiver lendo isso, souber como fazer o commit e push desses arquivos mais grandes, por favor, me ensine que eu mando esses arquivos)
Por conta disso, nesse Git estão só os arquivos que tive que modificar para abrir o jogo como uma view com o Android Studio. O qual irei explicar o passo a passo.

# Como Exportar o projeto Unity para o Android Studio
Tendo finalizado seu projeto no Unity, vá em:
File > Build Profiles > Em Platforms, selecione Android > Marque a Checkbox "Export Project" > Se for publicar no Google Play, marque a CheckBox "Export for App Bundle" > Salve em uma nova pasta vazia

Para Importar no Android Studio:
1. Vá em File > Import Module > Selcione a pasta "unityLibrary" do diretório de onde salvou o Export do Unity
2. Adicione <implementation project(':unityLibrary')> nas dependencies no arquivo build.gradle do app.
3. Adicione:
   <include ':app'
   include ':unityLibrary'
   include ':unityLibrary:mobilenotifications.androidlib'>
   no arquivo setting.gradle.
4. no arquivo AndroidManifest.xml, adicione esta activity:
   <activity
   android:name="com.unity3d.player.UnityPlayerGameActivity"
   android:label="UnityPlayerActivity"
   android:screenOrientation="landscape" // pode mudar para portrait, dependendo do tipo de jogo
   tools:replace="android:screenOrientation" />
5. Feito isso, pode chamar o jogo como uma Activity no Android Studio, como exemplificado no arquivo MainActivity.java desse repositório
OBS: É possível que seja necessário também modificar os arquivos build.gradle e AndroidManifest.xml dentro de unityLibrary. Dependendendo das configurações do Unity antes de realizar o Export. Além disso, o emulador do Android Studio não funciona para rodar os jogos de Unity, sendo necessário usar um dispositivo físico ou outro emulador externo ao Android Studio.

# Dicas do Unity
Bons sites para Template: Itch.io e Loja de assets da Unity.
App para facilitar testes do app com dipositivos móveis: Unity Remote (não precisa dar Build para testar a Scene)
Curso que me serviu de base para criar o jogo (foi minha primeira vez criando um jogo): https://www.youtube.com/watch?v=VdfdAvMj3qA&list=PLk7v1Z2rk4hjD-53VX9uqX_e6lZF9wSOX
