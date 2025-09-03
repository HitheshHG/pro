<script>
    import Github from "$lib/components/github.svelte";
    import Navbar from "$lib/components/navbar.svelte";
    import Footer from "$lib/components/footer.svelte";
    import Hero from "$lib/components/hero.svelte";

    import "../styles.css";
</script>

<svelte:head>
    <title>Hithesh HG | Portfolio</title>
    <meta name="description" content="Portfolio of Hithesh H.G, CSE student at NMAMIT, aspiring Web Developer and ML enthusiast.">
</svelte:head>

<Navbar />
<Hero />
<Github id="projects" />
<Footer />
