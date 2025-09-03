<script>
    import { onMount } from "svelte";

    import Fa from "svelte-fa";
    import {
        faStar,
        faCodeFork,
        faUpRightFromSquare,
    } from "@fortawesome/free-solid-svg-icons";
    import { faGithub } from "@fortawesome/free-brands-svg-icons";

    let data = [];
    let errorMessage = "";

    async function fetchRepoData() {
        const apiUrl = `https://api.github.com/repos/BrendanGlancy/dev-port`;

        try {
            const response = await fetch(apiUrl, {
                headers: {
                    Accept: "application/vnd.github.v3+json",
                },
            });

            if (!response.ok) {
                throw new Error(`Error: ${response.status}`);
            }

            data = await response.json();
        } catch (error) {
            errorMessage = "Failed to fetch profile";
            console.log(error);
        }
    }

    onMount(() => {
        fetchRepoData();
    });
</script>

<section>
    {#if errorMessage}
        <p class="error">{errorMessage}</p>
    {:else}
        <footer class="footer-container">
            <div class="footer-section">
                <h3>Articles</h3>
                <ul>
                    <li>
                        <strong>Stepping Onto the Stage</strong>
                        <a
                            href="https://medium.com/@gurudattajr/stepping-onto-the-stage-d5eedd507207"
                            ><Fa icon={faUpRightFromSquare} /></a
                        >
                        <p>published on medium</p>
                    </li>
                    <li>
                        <strong>2 Years of Engineering Journey</strong>
                        <a
                            href="https://medium.com/@gurudattajr/2-years-of-engineering-journey-d61484041747"
                            ><Fa icon={faUpRightFromSquare} /></a
                        >
                        <p>published on medium</p>
                    </li>
                </ul>
            </div>

            <div class="footer-section">
                <h3>LOCATION</h3>
                <div class="map-container">
                    <!-- svelte-ignore a11y_missing_attribute -->
                    <iframe src="https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d17122.803541700556!2d74.93272523842224!3d13.1738516963901!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3bbb56415ad85e5b%3A0x10b77ac6f6afc7fa!2sNitte%20Mahalinga%20Adyantaya%20Memorial%20Institute%20of%20Technology!5e0!3m2!1sen!2sin!4v1756912292160!5m2!1sen!2sin" width="600" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
                </div>
            </div>

            <div class="footer-section">
                <h3>SOCIAL</h3>
                <div class="social-links">
                    <a href="https://www.linkedin.com/in/hitheshhg/">LinkedIn</a
                    >
                    <a href="https://x.com/@gurudattajr">X</a>
                </div>
            </div>
            <div class="footer-bottom">
                <p>&copy; 2025 Hithesh HG | All Rights Reserved.</p>
            </div>
        </footer>
    {/if}
</section>

<style>
    .footer-container {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        padding: 3rem;
        background: radial-gradient(circle, #0c1019, #0d1117, #000);
        color: #c9d1d9;
        font-family: sans-serif;
        animation: gradientAnimation 80s infinite;
    }

    a {
        color: #8b949e;
        text-decoration: none;
    }

    .footer-section {
        flex: 1 1 25%;
        margin: 1.5rem;
        padding: 1.5rem;
    }

    .footer-section h3 {
        font-size: 1.2rem;
        margin-bottom: 1rem;
    }

    .footer-section ul {
        list-style: none;
        padding: 1rem;
    }

    .footer-section ul li {
        margin-bottom: 1rem;
    }

    .footer-section ul li p {
        font-size: 0.9rem;
        margin: 0.2rem 0 0;
        color: #8b949e;
    }

    .footer-section .social-links a {
        margin-right: 1rem;
        text-decoration: none;
        color: #c9d1d9;
        font-size: 1.2rem;
    }

    .footer-section .social-links a:hover {
        color: #58a6ff;
    }

    .footer-bottom {
        flex: 1 1 100%;
        text-align: center;
        margin-top: 2rem;
        font-size: 0.9rem;
        color: #8b949e;
    }

    .footer-bottom p {
        margin: 0.5rem 0;
    }

    @keyframes gradientAnimation {
        0% {
            background-position: 0% 50%;
        }
        50% {
            background-position: 100% 50%;
        }
        100% {
            background-position: 0% 50%;
        }
    }

    /* Mobile Styling */
    @media (max-width: 768px) {
        .footer-container {
            flex-direction: column;
            padding: 1rem;
        }

        .footer-section {
            flex: 1 1 100%;
            margin: 1rem 0;
            padding: 1rem;
        }

        .footer-section h3 {
            font-size: 1rem;
        }

        .footer-section ul li p {
            font-size: 0.8rem;
        }

        .footer-section .social-links a {
            font-size: 1rem;
        }

        .footer-bottom {
            margin-top: 1rem;
        }
    }
</style>
