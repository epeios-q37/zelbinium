---
title: Accueil
menu: Accueil
weight: 1
---

<!-- Attention : 'home.md' est un lien symbolique vers '_index.md' ! -->
<!-- Les URL doivent être absolues !!! -->



<!--
<div style="margin-bottom: 10px; background-color: green; font-size: larger; padding: 10px;">
  <span style="display: flex;">
    <a style="background-color: white; color: green; border-radius: 20px; font-family: sans-serif; font-weight: bold; padding: 5px 30px; margin: 10px auto" href="../support">Soutenez <em>Zelbinium</em></a>
  </span>
</div>
-->

<!--[![](AnimatedLogo.gif)](../support)-->

<style>
#rotate-words:has(div) {
  background-color:#3757D0;
  background-image:radial-gradient(#81BCFF, #303391);
  background-repeat:no-repeat;
  background-attachment:fixed;
  border-radius: 50%;
  color:#fff;
  text-align:center;
}

#rotate-words {
  margin:auto;
  padding:5% 0;
  font-size:20px;
  text-transform: capitalize;
  text-shadow: #FC0 1px 0 10px;
}

#rotate-words div {
  position:relative;
  opacity: 0;
  overflow:hidden;
  line-height:1.2em;
  animation: rotate-word 8s linear infinite 0s;
}

@keyframes rotate-word {
  0% { opacity: 0;  transform: translateX(0);filter:blur(10px);transform:scale(.8)}
  10% { opacity: 1;  transform: translateX(0);filter:blur(0px);transform:scale(.9)}
  30% { opacity: 1; transform: translateX(0);filter:blur(0px);transform:scale(1)}
  50% { opacity: 0; transform: translateX(0);filter:blur(10px);transform:scale(1.2)}
  80% { opacity: 0}
  100% { opacity: 0}
}

#rotate-words div:nth-child(1) { animation-delay: 4s}
#rotate-words div:nth-child(2) { animation-delay: 8s}
</style>

<div>
  <div id="rotate-words">  
    <div>Passez au niveau supérieur !</div>
    <div>Utilisez vos propres applications !</div>
  </div>
</div>

Exploitez tout le potentiel de vos appareils numériques  :
- créez vos propres véritables [applications connectées](https://fr.wikipedia.org/wiki/Applicaion_web) pour et avec votre smartphone, tablette, ordinateur personnel… ;
- partagez-en l'accès immédiat à l'aide d'un [code QR](https://fr.wikipedia.org/wiki/Code_QR) ou avec votre application de messagerie [électronique](https://fr.wikipedia.org/wiki/Courrier_%C3%A9lectronique) ou [instantanée](https://fr.wikipedia.org/wiki/Messagerie_instantan%C3%A9e) préférée.

<div style="text-align: center; width: 100%;">
  <!-- Fait avec https://imagemapper.pageballoon.com/#/ -->
  <svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 868 403">
    <image width="868" height="403" xlink:href="Incitation.png"></image> <a xlink:href="../action">
      <rect x="0" y="0" fill="#fff" opacity="0" width="520" height="202"></rect>
    </a><a xlink:href="../action">
      <rect x="0" y="205" fill="#fff" opacity="0" width="205" height="198"></rect>
    </a><a xlink:href="../inspiration">
      <rect x="523" y="0" fill="#fff" opacity="0" width="345" height="212"></rect>
    </a><a xlink:href="../inspiration">
      <rect x="214" y="212" fill="#fff" opacity="0" width="654" height="191"></rect>
    </a>
  </svg>
  <div style="font-size: small;">
    <span>Crée avec </span>
    <a href="https://framalab.org/gknd-creator/" target="_blank">
      <em>GéGé</em></a><span>.</span>
  </div>
</div>

*Cliquez sur les phylactères ou utilisez le menu.*

<!--
- [*Action !*](../action) : section montrant les différentes actions réalisables sur le code source d'une application simplement à partir de votre navigateurs web ;
- [*Inspiration*](../inspiration) : section comprenant des applications que vous pouvez modifier à partir de votre navigateur web et dont vous pouvez vous inspirer pour créer vos propres applications.
-->