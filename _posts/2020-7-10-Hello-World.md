---
layout: post
title: Welcome to The Dark Red Tower
---
<html>

    <a href="/projects.html"><button class="button button1">Projects</button></a>
    <a href="/code.html"><button class="button button2">Code</button></a>
<style>
.button {
  padding: 50px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  margin-left: 10%;
  margin-right: 10%;
  margin-top: 5%;
    margin-bottom: 2%;
  width: 80%;
}

html, body {
  height: 100%;
}

.wrap {
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.button {
  min-width: 300px;
  min-height: 60px;
  font-family: monospace;
  font-size: 22px;
  text-transform: uppercase;
  letter-spacing: 1.3px;
  font-weight: 700;
  color: white;
  background: linear-gradient(180deg, rgb(136 5 5) 50%, rgb(0, 0, 0) 100%);
  border: none;
  border-radius: 1000px;
  box-shadow: 12px 12px 24px rgba(186, 198, 197, 0.64);
  transition: all 0.3s ease-in-out 0s;
  cursor: pointer;
  outline: none;
  position: relative;
  }

button::before {
content: '';
  border-radius: 1000px;
  min-width: 300px;
  min-height: 125px;
  border: 6px solid #fcfcfc;
  border-style: double;
  box-shadow: 0 0 60px rgba(222, 224, 223, 0.64);
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  opacity: 0;
  transition: all .3s ease-in-out 0s;
  width: 100%
}

.button:hover, .button:focus {
  color: grey;
  transform: translateY(-6px);
}

button:hover::before, button:focus::before {
  opacity: 1;
}

button::after {
  content: '';
  width: 30px; height: 30px;
  border-radius: 100%;
  border: 6px solid rgba(89, 99, 111, 0.72);
  position: absolute;
  z-index: -1;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  animation: ring 2.5s infinite;
}

button:hover::after, button:focus::after {
  animation: none;
  display: none;
}

@keyframes ring {
  0% {
    width: 30px;
    height: 30px;
    opacity: 1;
  }
  100% {
    width: 900px;
    height: 400px;
    opacity: 0;
  }
}
</style>
</html>


Welcome to The Dark Red Tower, a place where share information, opinions, code and more about a lot of technology topics. In this blog you con find two main cornets; one of them dedicated to my own projects, and the other one dedicated to my code shown also in GitHub.
If you want to know more about me and who I am, you can click in "About" to read some information about me. 
You can find information in spanish and in english here.
Enjoy!

<img src="/images/Th3RedTower.png" alt="_config.yml" style="
    display: block;
    margin-right: auto;
    margin-left: auto;
    margin-bottom: 20px;
    width: 80%;
">

Bienvenid@s a The Dark Red Tower, un lugar donde compartir información, opiniones, código y mucho más sobre temas tecnológicos. En este blog podrás encontrar dos principales rincones, uno de ellos dedicado a mis propios proyectos (projects), y el otro dedicado a mi código (code) publicado también en GitHub. 
Si quieres saber más sobre mí y quien soy, puedes hacer click en "About" para leer alguna información adicional.
Podrás encontrar información en español y en inglés aqui.

¡Disfruta!