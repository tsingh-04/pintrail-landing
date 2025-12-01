<script>
  import Header from './lib/Header.svelte';
  import { onMount } from 'svelte';

  // Countdown features
  const earthDay = new Date("2026-04-22T00:00:00");

  let countdown = $state("");

  function updateCountdown() {
    const now = new Date();
    const diff = earthDay.getTime() - now.getTime();

    if (diff <= 0) {
      countdown = "It's Earth Day!";
      return;
    }

    const days = Math.floor(diff / (1000 * 60 * 60 * 24));
    const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
    const minutes = Math.floor((diff / (1000 * 60)) % 60);
    const seconds = Math.floor((diff / 1000) % 60);

    countdown = `${days}d ${hours}h ${minutes}m ${seconds}s`;
  }

  onMount(() => {
    updateCountdown();
    const id = setInterval(updateCountdown, 1000);
    return () => clearInterval(id);
  });
</script>

<!-- Header -->
<Header title="PinTrails"/>

<!-- What Is It? -->
<section class="section">
  <p class="purpose">A mobile application promoting sustainability awareness at UMass Amherst by helping users detect and 
    explore digital artifacts across campus. Users can simply view the interactive map to see artifacts in their area, 
    receive notifications when passing by a site, and follow guided paths to explore connected sites and themed tours.</p>
</section>

<!-- Key Features -->
<section class="section">
  <h2 class="section-title">Key Features</h2>
    <p>🌍 Map-based site discovery</p>
    <p>🔔 Notifications when passing by sites</p>
    <p>🔎 Search artifacts by name, category, or proximity</p>
    <p>📸 View site media (photos, audio, documents, videos)</p>
    <p>🌲 Explore themed sustainability trails</p>
    <p>🧭 Create custom self-guided tours</p>
    <p>➡️ Navigate with Google Maps redirection</p>
    <p>📱 Mobile-friendly design</p>
</section>

<!-- Artifacts & Paths -->
<section class="section">
  <h2 class="section-title">Artifacts & Trails</h2>

  <div class="cards">
    <!-- ARTIFACTS CARD -->
    <article class="card">
      <h3>Artifacts</h3>

      <p>
        Artifacts are sustainability landmarks across campus that are displayed in the app as interactive map pins, 
        each containing photos, written descriptions, and links to related sites. Additional informative media types 
        may also be included.
      </p>

      <div class="card-image">
        <img
          src="RoofGarden.jpg"
          alt="Interactive map showing sustainability artifacts across campus"
        />
      </div>

      <p>This image is an example of the Roof Garden artifact, located at the Design Building</p>

    </article>

    <!-- TRAILS CARD -->
    <article class="card">
      <h3>Trails</h3>

      <p>
        Trails are a collection of artifacts that users can follow through self-guided tours. They may choose from 
        pre-built tours or create their own by selecting sites of interest. Tour themes include water, nature, built 
        environment, etc.
      </p>

      <div class="card-image">
        <img
          src="Trail.png"
          alt="Example of a self-guided sustainability tour"
        />
      </div>

      <p>This image is an example of a pre-built tour following a trail of renewable energy artifacts</p>

    </article>
  </div>
</section>  

<!--Purpose -->
<section class="section">
  <p class= "purpose">PinTrails supports place-based learning and sustainability awareness by making campus landmarks, resources, and 
    initiatives more accessible. It’s targeted towards individuals such as UMass students, educators, and visitors who 
    want to explore campus in a meaningful, interactive way. </p>
</section>

<!-- Footer -->
<footer>
  <h1>COMING SOON</h1>
  <h2>Earth Day 2026</h2>
  <h2 class="countdown">{countdown}</h2>
</footer>

<!-- Styling -->
<style>
  footer {
    margin-top: 80px;
    text-align: center;
    padding-bottom: 40px;
  }

  footer h2 {
    margin: 0;
    font-size: 1.4rem;
    letter-spacing: 0.1em;
    font-weight: 700;
  }

  .countdown {
    font-size: 1.1rem;
    font-weight: 600;
    margin-top: 6px;
  }

  .section {
  max-width: 1100px;
  margin: 3rem auto;
  padding: 0 1.5rem;
}

.section-title {
  text-align: center;
  font-size: 1.8rem;
  margin-bottom: 2rem;
}

.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 2rem;
}

.card {
  background: #111827;         
  border-radius: 1rem;
  padding: 1.75rem;
  box-shadow: 0 18px 40px rgba(0, 0, 0, 0.35);
}

.card h3 {
  font-size: 1.3rem;
  margin-bottom: 1rem;
}

.card-image {
  margin-bottom: 1rem;
  border-radius: 0.75rem;
  overflow: hidden;
}

.card-image img {
  display: block;
  width: 100%;
  height: auto;
}

.card p {
  line-height: 1.7;
}

.purpose {
  font-size: 1.2rem;
}
</style>
