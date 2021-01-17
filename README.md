# Instalação
Digite no terminal o seguinte:
``npm install round-api.js``
# Sobre
 O round-api.js é uma blibioteca feita para iniciantes no discord.js, que querem apenas um bot de música sem saber básicamente nada de programação... (você pode dar play em uma musica com apenas 1 linha)
Desenvolvido pela Nex Group. Um grupo de programadores focados em ajudar ao proximo!
# Iniciando
Para iniciar siga os passos abaixo.
em seu arquivo de comando você primeiro precisa declarar á nossa blibioteca assim:

Key para testar: ``atMpLrWdXaVrrJRA3k``
```js
const round = require("round-api.js");
//Depois de declarar basta criar uma instancia assim:
const music = new round("sua-key", client) //Key gerada no site https://dashboard.roundbot.tk/ e o "client" é o seu bot, ou seja á instancia que você fez para o client exemplo:
const client = new Discord.Client();
```
# Propiedades e funções (Sem comentarios)
```js
music.play(message, args, (song) => {});
music.stop(message, () => {});
music.loop(message, args, (song) => {});
music.skip(message, () => {});
music.pause(message, () => {});
music.resume(message, () => {});
music.lyrics(message, (song) => {});
music.queue(message, (song) => {});
music.jump(message, args, (song) => {});
music.volume(message, args, (song) => {});
```
# Propiedades e funções
```js
//Play
music.play(message, args, (song) => {
    //song é um objeto, que traz todas as informações sobre á musica escolhida pelo usuário;
    /* Objecto do song
    song: {
        id: "id da musica",
        title: "titulo da musica",
        url: "url da musica",
        img: "thumbnail da musica",
        duration: "duracao da musica em segundos",
        ago: "data em qual a musica foi publicada",
        views: "mostra as views da musica",
        req: {} //Retorna o objeto do usuario.
    }
    */ //Exemplo de uma embed simples :3
    const embed = new Discord.MessageEmbed()
    .setTitle(song.title)
    .setDescription(`Tocando á musica: ${song.title}\nRequisitada por ${song.req.username}`)
    .setThumbnail(song.img)
    .setColor("BLACK")
    .setFooter(`${song.views} views`)
    message.channel.send(embed);
});
//Stop
music.stop(message, () => {
    //Embed ou mensagem... o stop não possue retorno :3
});
//Skip
music.skip(message, () => {
   //Embed ou mensagem... o skip não possue retorno :3 
});
//Pause
music.pause(message, () => {
    //Embed ou mensagem... o pause não possue retorno :3
});
//Resume
music.resume(message, () => {
    //Embed ou mensagem... o resume não possue retorno :3
});
//Loop
music.loop(message, (song) => {
    //Embed ou mensagem... o objeto song retorna apenas o estado do loop, se ele está ativado ou desativado
    /* Objeto do song (no loop)
    song: {
        state: "ativado/desativado" //ativado ou desativado
    }
    */ // Exemplo de uma embed simples :3
    const embed = new Discord.MessageEmbed()
    .setDescription(`O loop está: ${song.state}`)
    message.channel.send(embed);
});
//Lyrics
music.lyrics(message, () => {
    //Embed ou mensagem... o objeto song é retornado com algumas informaçoes
    /*Objeto do song (no lyrics)
        song: { 
            lyrics: "Letra",
            image: "thumbnail",
            title: "titulo"
        }
    */
});
//Queue
music.queue(message, args, async (song) => {
    //Embed... no queue faremos um pouco diferente, precisamos declarar o nosso client.embed para não ocorrer erros, lembrando que é obrigatorio caso contrario o queue não ira retornar nada :3 (vamos resolver na proxima atualização)
    //Embed simples :3
    client.embed = await new Discord.MessageEmbed()
    .setAuthor("Fila de musicas", "https://raw.githubusercontent.com/SudhanPlayz/Discord-MusicBot/master/assets/Music.gif")
    .setThumbnail(message.guild.iconURL())
    .setColor("BLUE")
    .setDescription(`${song.description}`)
    .addField("Tocando agora", song.playing, true)
    .addField("Canal Solicitado", song.channel.text, true)
    .addField("Canal de voz", song.channel.voice, true)
    .setFooter("O volume atual é " + song.volume);
    //Lembrando que no queue não precisamos enviar para o canal, ele sera enviado automaticamente pelo nosso modulo de exportação :3
})
//Jump
music.jump(message, args, (song) => {
    //Embed ou mensagem... o objeto song retorna á posição da fila :3
    /*Objeto song (no jump)
    song: {
        position: "posição"
    }
    */
})
//Volume
music.volume(message, args, (song) => {
    //Embed ou mensagem... o objeto do song retorna o valor do volume :3
    /*Objeto son (no volume)
    song: {
        value: "valor"
    }
    */
})
```
# Syntax
Á syntax da nossa blibioteca é a mesma em todas funções, totalmente orientada á objetos.
```js
//Syntax
instance.property(params, callbacks());//instancia.propiedade(parametro, chamadas());
```

Qualquer dúvida ou erro entrar em contato com á nossa equipe pelo discord:
https://discord.gg/amYQNpTRaw
Ou entrar em contato diretamente com o CEO da nossa equipe e desenvolvedor de todas as blibiotecas nex:
``Purplex#1125`` or CTO ``Jeff '-'#0374``

Obrigado!
