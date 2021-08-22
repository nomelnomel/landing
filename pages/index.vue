<template>
  <div id="app">
    <header>
      <div class="logo">Лого</div>
      <div class="header-item">Купить приглашение</div>
      <div v-scroll-to="'#faq'" class="header-item">faq</div>
    </header>
    <div class="form">
      <div class="form-start">
        <input type="text" placeholder="введите имя" />
        <input type="text" placeholder="введите фамилию" />
      </div>
      <small-form v-for="n in counter" :key="n" />
      <button @click="addMember">добавить участника</button>
      <button @click="delLastMember">удалить последнего участника</button>
    </div>
    <div class="first-block">
      <div class="main">
        <div class="text">
          <h2>bienvenue en russie!</h2>
          <p>
            Enfin! La Russie a repris la délivrance de tous les types de visas à
            toute personne de nationalité française et aux ressortissants de
            pays tiers qui ont le droit de séjour permanent en France.
          </p>
          <p>
            Pour effectuer un voyage touristique en Russie, il faut obtenir le
            visa. Et pour le faire il est nécessaire d’avoir une invitation
            également connue comme le voucher. Commandez ce document sur notre
            site pour obtenir votre visa russe.
          </p>
        </div>
        <nuxt-link to="/commander" class="btn btn-order">Commander</nuxt-link>
      </div>
    </div>

    <div class="second-block container">
      <div class="main">
        <div class="text">
          <h3>Qu’est-ce que c’est un voucher?</h3>
          <p>
            L’invitation touristique pour la Russie est un des documents
            nécessaires afin d’obtenir votre visa touristique russe.
          </p>
          <p>
            Il consiste de deux parties: le voucher touristique et la
            confirmation d’accueil d’un tour-opérateur russe.
          </p>
          <p>
            Faites attention que le tour-opérateur doive être inscrit auprès du
            Registre fédéral des tour-opérateurs.
          </p>
        </div>
        <div class="image">
          <img src="/Exemple.png" alt="" />
        </div>
      </div>
      <div class="btn">Commander</div>
    </div>

    <div class="third-block container">
      <div class="main">
        <span>Vous nous envoyez vos donnés et faites le paiement</span>
        <img src="/right.svg" alt="" />
        <span>Vous recevez votre invitations touristique sous 24 heures</span>
        <img src="/right.svg" alt="" />
        <span>
          Vous déposez votre dossier au centre des visas russe et obtenez votre
          visa
        </span>
        <img src="/right.svg" alt="" />
        <span>Bienvenue en Russie!</span>
      </div>
    </div>

    <div class="forth-block container">
      <h3>Tarifs</h3>
      <p>
        Etant le tour-opérateur officiel nous pouvons vous proposer le meilleur
        tarif pour le voucher touristique pour la Russie :
      </p>
      <ul>
        <li>1-3 voyageurs = 20 euros par invitation</li>
        <li>4-7 voyageurs = 17 euros par invitation</li>
        <li>8+ voyageurs = 15 euros par invitation</li>
      </ul>
      <p>
        N’hésitez pas à nous demander un tarif spécial pour un groupe de plus de
        15 voyageurs.
      </p>
    </div>

    <div class="fifth-block container">
      <h3>Qui peut venir?</h3>
      <p>
        Selon les règles du gouvernement français, pour faire un voyage
        touristique en Russie il faut être complètement vacciné par des vaccins
        reconnus par l’EMA (Pfizer/Comirnaty, Moderna,
        AstraZeneca/Vaxzevria/Covishield, Janssen).
      </p>
      <p>Voici les conditions des voyages à destination de la Russie:</p>
      <Spoiler :items="rules" />
    </div>

    <div class="faq-block container">
      <h3>F.A.Q.</h3>
      <Spoiler :items="questions" />
    </div>
    <div class="reviews">
      <swiper ref="mySwiper" :options="swiperOptions">
        <swiper-slide v-for="(review, i) in reviews" :key="i">
          <h2>{{ review.text }}</h2>
          <p>{{ review.author }}</p>
        </swiper-slide>
        <div slot="pagination" class="swiper-pagination"></div>
      </swiper>
    </div>
  </div>
</template>

<script>
import { Swiper, SwiperSlide, directive } from 'vue-awesome-swiper'
import SmallForm from '@/components/SmallForm'
import Spoiler from '@/components/Spoiler'
import 'swiper/css/swiper.css'
export default {
  name: 'App',
  components: {
    Swiper,
    SwiperSlide,
    SmallForm,
    Spoiler,
  },
  directives: {
    swiper: directive,
  },
  data() {
    return {
      forms: [],
      formId: 0,
      counter: 0,
      swiperOptions: {
        slidesPerView: 1,
        pagination: {
          el: '.swiper-pagination',
          clickable: true,
        },
        autoplay: {
          delay: 6000,
          disableOnInteraction: false,
          pauseOnMouseEnter: true,
        },
        loop: true,
      },
      rules: [
        {
          id: 1,
          title: 'Je suis vacciné et j’ai mon',
          text: 'Afin de partir en Russie il vous faut avoir la preuve de vaccination et un test PCR négatif effectué au plus tard 72 heures avant l’arrivée en Russie. Le test doit être traduit en anglais ou en russe. Et bien sûr votre visa russe. A votre retour en France aucun test ni quarantaine ne sont demandés.',
          show: false,
        },
        {
          id: 2,
          title: 'Je ne suis pas vacciné',
          text: "Dans ce cas vous devez disposer d'un motif impérieux de séjour en Russie et observer une quarantaine de 10 jours à votre retour en France",
          show: false,
        },
      ],
      questions: [
        {
          id: 1,
          title: 'Вопрос 1',
          text: 'Ответ на вопрос 1',
          show: true,
        },
        {
          id: 2,
          title: 'Вопрос 2',
          text: 'Ответ на вопрос 2',
          show: false,
        },
      ],
      reviews: [
        {
          author: 'Reinhardt',
          text: "Nous avons obtenu nos visas sans aucun souci. Votre agence et tout le personnel mérite 20 sur 20, et croyez moi... c'est une note que je n'ai pas mise souvent dans ma longue carrière d'enseignant.",
        },
        {
          author: 'Véronique',
          text: 'Un petit mot pour vous remercier pour la qualité des prestations fournies. J’ai apprécié votre efficacité et rapidité, tout s’est déroulé comme annoncé et j’ai déjà mon visa.',
        },
        {
          author: 'Nathalie et Thierry',
          text: 'Nous voulions vous remercier très sincèrement pour l’ensemble de vos prestations. Les documents sont arrivés à l’heure et nous avons déposé le dossier comme prévu. Merci surtout d’avoir répondu à toutes nos questions sur la procédure d’obtention de visa.',
        },
      ],
    }
  },
  methods: {
    addMember() {
      this.counter++
    },
    delLastMember() {
      this.counter--
    },
  },
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Oxygen:wght@300&display=swap');

.first-block {
  background: url('/crem.jpg') 50% 50% no-repeat;
  background-size: cover;
  display: flex;
  justify-content: flex-end;
  width: 100%;
  padding: 75px 0 45px;
  position: relative;

  &:after {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(255, 255, 255, 0.5);
  }

  .main {
    display: flex;
    flex-direction: column;
    max-width: 50%;
    padding: 70px 120px 30px 100px;
    border: 10px solid black;
    border-right: none;
    position: relative;
    z-index: 2;

    @media screen and (max-width: 1440px) {
      max-width: 66%;
    }

    h2 {
      font-size: 80px;
      line-height: 80px;
      text-transform: uppercase;
      font-weight: bold;
      margin-bottom: 20px;
    }

    p + p {
      margin-top: 20px;
    }
  }
}

.second-block {
  padding: 50px;
  display: flex;
  flex-direction: column;
  align-items: center;

  .main {
    display: flex;
    justify-content: space-between;
    .text {
      width: 50%;
      align-self: center;
      margin-right: 50px;

      h3 {
        margin-bottom: 30px;
      }
      p + p {
        margin-top: 20px;
      }
    }

    .image {
      width: 50%;
      img {
        width: 100%;
        border: 1px solid black;
      }
    }
  }
}

.third-block {
  .main {
    display: flex;
    align-items: center;
    justify-content: space-between;
    span {
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 30px;
      width: 250px;
      height: 250px;
      border: 3px solid blue;
      border-radius: 50%;
      margin: 0 30px;
      font-size: 20px;
    }

    img {
      width: 60px;
    }
  }
}

.forth-block {
}

.btn {
  cursor: pointer;
  color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  text-transform: uppercase;
  border: none;
  background: red;
  font-size: 30px;
  padding: 20px 30px;
  align-self: center;
  border-radius: 10px;
  margin-top: 30px;
}
.swiper-container {
  max-width: 700px;
  margin: 0 auto;
}

.swiper-slide {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  flex-direction: column;
}

.reviews h2 {
  text-shadow: none;
  color: black;
  margin-bottom: 20px;
}

.reviews p {
  color: #bababa;
}

.swiper-container {
  padding-bottom: 70px;
}
</style>
