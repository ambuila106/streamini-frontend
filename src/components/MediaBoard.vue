<template>
  <div class="media-board">
    <br>
    <span class="text-20 ls-1">La plataforma para los cinefilos y críticos</span>

    <div class="medias">
      <div v-for="media in [0, 1, 3, 4, 5, 6]" class="media" :key="media">
        <img src="../assets/img/barbie-cartel.jpg" alt="">
        <span class="pt-2">Barbie the movie</span>
        <div class="media-statistics text-16">
          <span class="pr-1">300M ⭐</span>
          <span class="pr-1">3.8 👁️</span>
          <div class="options">
            ☰
            <div class="tooltiptext">
              <div class="ec-stars-wrapper">
                <a v-for="point in [1,2,3,4,5]" :key="point" @click="updateReview(point, media)" data-value="1" title="Votar con 1 estrellas">&#9733;</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MediaBoard',
  props: {
    msg: String
  },
  data() {
    return {
      medias: []
    }
  },

  methods: {
    getMedias() {
      fetch('http://localhost:8000/api/medias/medias')
      .then(response => {
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        return response.json(); // Assuming the response is JSON
      })
      .then(data => {
        // Use the data returned from the server
        this.medias = data
      })
      .catch(error => {
        // Handle any errors that occurred during the fetch.
        console.error('There was a problem with the fetch operation:', error);
      });
    },

    updateReview(rating, id) {
      const formData = new FormData();

      formData.append('rating', rating);

      const params = new URLSearchParams(formData);

      fetch(`https://localhost:8080/api/medias/medias/${id}/update-rating/`, {
        method: 'POST',
        body: params
      })
      .then(response => {
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        return response
      })
      .then(data => {
        console.log(data)
      })
      .catch(error => {
        console.error('There was a problem with the fetch operation:', error)
      })
    },

    updateWatched(id) {
      fetch(`https://localhost:8080/api/medias/medias/${id}/mark_as_watched/`, {
        method: 'POST',
      })
      .then(response => {
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        return response
      })
      .then(data => {
        console.log(data)
      })
      .catch(error => {
        console.error('There was a problem with the fetch operation:', error)
      })
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .media-board {
    height: 100vh;
    width: 100%;
    color: white;
  }

  .text-20 {
    font-size: 20px;
  }

  .ls-1 {
    letter-spacing: 1px;
  }

  .media {
    width: 200px;
    margin-right: 12px;
    display: flex;
    flex-direction: column;
    color: white;
    padding-bottom: 20px;
  }

  .media img {
    width: 100%;
    border-radius: 5px;
    object-fit: cover;
  }

  .medias {
    padding-top: 60px;
    display: flex;
    flex-wrap: wrap;
    padding: 20px 10%;
  }

  .pt-2 {
    padding-top: .5rem;
  }

  .text-16 {
    font-size: 14px;
  }

  .pr-1 {
    padding-right: .5rem;
  }

  .media-statistics {
    justify-content: center;
    display: flex;
  }


  .options {
    position: relative;
    display: inline-block;
    border-bottom: 1px dotted black;
  }

  .options .tooltiptext {
    visibility: hidden;
    width: 150px;
    background-color: black;
    color: #fff;
    text-align: center;
    border-radius: 6px;
    padding: 5px 0;

    /* Position the tooltip */
    position: absolute;
    z-index: 1;
  }

  .options:hover .tooltiptext {
    visibility: visible;
  }



  /* Estilos CSS sin procesar equivalente al código SCSS */

.ec-stars-wrapper {
  font-size: 0;
  display: inline-block;
}

.ec-stars-wrapper a {
  text-decoration: none;
  display: inline-block;
  font-size: 24px;
  font-size: 2rem;
  color: #888;
  transition: text-shadow 0.5s ease;
  text-shadow: 0 0 0 rgba(0, 0, 0, 0.3);
}

.ec-stars-wrapper:hover a {
  color: rgb(234, 190, 63);
  text-shadow: 0.1em 0.1em 0.2em rgba(0, 0, 0, 0.3);
}

.ec-stars-wrapper > a:hover ~ a {
  color: #888;
  text-shadow: none;
}

</style>
