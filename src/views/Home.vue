<template>
  <div>
    <div id="home">
      <div>
        <img alt="Profile Pic" src="../assets/gael.leroy.png" class="profilePic">
        <h1>Gaël Leroy développeur étudiant</h1>
        <link rel="stylesheet" 
        href="https://use.fontawesome.com/releases/v5.2.0/css/all.css" 
        integrity="sha384-hWVjflwFxL6sNzntih27bfxkr27PmbbK/iSvJ+a4+0owXq79v+lsFkW54bOGbiDQ" 
        crossorigin="anonymous">
        <div style="padding-bottom: 15px; padding-top: 5px;">
            <a href="https://github.com/g-lgtm">
              <i class="icon fab fa-github fa-2x"/>
            </a>
            <span style="padding: 10px;"/>
            <a href="https://www.linkedin.com/in/ga%C3%ABl-leroy-449932199/">
              <i class="icon fab fa-linkedin-in fa-2x"/>
            </a>
        </div>
        <div></div>
        <button @click="goTo('Contact')" class="contactButton">Contacter</button>
      </div>
    </div>
    <div id="about">
      <div style="color: black;">
        <p>
          Je suis un étudiant français qui aime la logique et programmer.
        </p>
        <p>
          J'aime écrire des programmes pour résoudre des problèmes ou, tout simplement, pour automatiser une tache que je trouverais trop répétitive.
          Donc j'aime énormément tout ce qui est programmes utiles et gestion de données.
        </p>
        <p>
          J'aime aussi apprendre sur les ordinateurs, faire du design (le web, tout comme les jeux vidéo, est extrêmement intéressant et a des possibilités infinies.). La récursion est une façon de coder qui m'intrigue et que j'aime pratiquer. (et une légère attirance pour la crypto).<br>
        </p>
        <p>
          Enough about what I like, let's see what I've done and what I can do.
        </p>
        <div style="padding: 5%">
          <img src="https://github-readme-stats.vercel.app/api?username=g-lgtm&count_private=true&show_icons=true&include_all_commits=true" width="350px">
        </div>
      </div>
    </div>
    <div id="experience">
      <div>
        <table>
          <tr>
            <th>Date</th>
            <th>Infos</th>
          </tr>
          <tr>
            <td class="stickRight">Septembre 2021</td>
            <td>Participation à un hackathon à Inria</td>
          </tr>
          <tr>
            <td class="stickRight">Juin - Décembre 2020</td>
            <td>Stage d'informatique à PG3</td>
          </tr>
          <tr>
            <td class="stickRight">Novembre 2019</td>
            <td>Gagnant du prix geek lors du Hackathon Greentech</td>
          </tr>
          <tr>
            <td class="stickRight">Avril 2017</td>
            <td>Stage de cuisine à La bastide de Tourtour</td>
          </tr>
          <tr>
            <td class="stickRight">Été 2016</td>
            <td>Différents extra en pâtisserie à la gloire de mon père</td>
          </tr>
          <tr>
            <td class="stickRight">Juin 2016</td>
            <td>Stage de cuisine à la gloire de mon père</td>
          </tr>
          <tr>
            <td class="stickRight">Decembre 2014</td>
            <td>Stage en service à la gloire de mon père</td>
          </tr>
        </table>
        <span class="paddTab"/>
        <table>
          <tr>
            <th>Date</th>
            <th>Infos</th>
          </tr>
          <tr>
            <td class="stickRight">2019 - 2024</td>
            <td>Diplome d'excellence en ingénieurie de l'informatique École Epitech - Nice</td>
          </tr>
          <tr>
            <td class="stickRight">Juillet 2021</td>
            <td>formation sur la Data IA</td>
          </tr>
          <tr>
            <td class="stickRight">2015 - 2018</td>
            <td>BAC technologique hôtellerie restauration lycée Paul Augier</td>
          </tr>
          <tr>
            <td class="stickRight">2015</td>
            <td>Brevet des collèges Marie Mauron</td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  methods: {
    goTo(path) {
        if (path == "Contact" && this.$router.currentRoute.path != "/Contact")
          this.$router.push(path);
        else if (path != "Contact" && this.$router.currentRoute.path != "/")
          this.$router.push('/');
    },
  }
}
</script>

<style>

#home {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(338deg, #a1c4fd, #667eea, #764ba2);
}

.profilePic {
  width: 15%;
  border: 1px solid white;
  border-radius: 100%;
}

.contactButton {
  border: 1px hidden black;
  border-radius: 100px;
  padding: 10px;
  padding-left: 30px;
  padding-right: 30px;
}

.contactButton:hover {
  cursor: pointer;
  animation: scaleAnim 0.5s;
}
@keyframes scaleAnim {
  0%{transform: scale(1);}
  50%{transform: scale(0.75);}
  100%{transform: scale(1);}
}

.icon {
  /* padding-left: 10px;
  padding-right: 10px; */
  width: 35px;
  color: black;
}

.icon:hover {
  cursor: pointer;
  color: #ffa500;
  animation: yellowscale 0.4s;
  transform: scale(1.25);
}
@keyframes yellowscale {
  0%{transform: scale(1); color: black;}
  100%{transform: scale(1.25); color: #ffa500;}
}

.goDown {
  color: black;
  position: fixed;
  bottom: 0;
}

#about {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: rgb(255,248,235);
  background: #F0E8DB;

}

#experience {
  height: 100vh;
  color: black;
  background-color: #764ba2;
    
  display: flex;
  justify-content: center;
  align-items: center;
}

table {
  background-color: #8080808e;
  border-radius: 10px;
}

.stickRight {
  display: flex;
  justify-content: right;
  align-items: right;
  padding-right: 10px;
}

.paddTab {
  padding: 10px;
}

td {
  padding: 10px;
  padding-bottom: 0;
}

</style>