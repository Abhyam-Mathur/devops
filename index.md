<style>
	:root {
		--bg: #f4f7fb;
		--card: #ffffff;
		--text: #10233b;
		--muted: #4c6077;
		--accent: #0078d4;
		--accent-soft: #e8f3ff;
		--border: #d7e4f2;
	}

	body {
		background: radial-gradient(circle at top right, #e6f2ff 0%, var(--bg) 55%);
		color: var(--text);
	}

	.hero {
		background: linear-gradient(135deg, #0b2f56 0%, #0e4d8a 100%);
		color: #fff;
		border-radius: 16px;
		padding: 24px;
		margin: 12px 0 18px;
		box-shadow: 0 8px 24px rgba(10, 40, 72, 0.22);
	}

	.hero h1 {
		margin: 0;
		font-size: 2rem;
		letter-spacing: 0.4px;
	}

	.hero p {
		margin: 8px 0 0;
		color: #dbeaff;
	}

	.meta {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(210px, 1fr));
		gap: 10px;
		margin: 18px 0 8px;
	}

	.chip {
		background: var(--accent-soft);
		border: 1px solid #c7def8;
		border-radius: 12px;
		padding: 10px 12px;
		font-size: 0.95rem;
		color: #12385f;
	}

	.grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		gap: 12px;
		margin-top: 14px;
	}

	.card {
		background: var(--card);
		border: 1px solid var(--border);
		border-radius: 14px;
		padding: 14px;
		box-shadow: 0 4px 14px rgba(16, 35, 59, 0.08);
	}

	.card h3 {
		margin: 0 0 8px;
		font-size: 1.05rem;
		line-height: 1.35;
	}

	.card p {
		margin: 0 0 10px;
		color: var(--muted);
		font-size: 0.95rem;
	}

	.button {
		display: inline-block;
		text-decoration: none;
		background: var(--accent);
		color: #fff;
		padding: 6px 12px;
		border-radius: 999px;
		font-size: 0.9rem;
		font-weight: 600;
	}
</style>

<section class="hero">
	<h1>DevOps Laboratory</h1>
	<p>Containerization and DevOps Lab experiments with documented implementation and outcomes.</p>
</section>

<div class="meta">
	<div class="chip"><strong>Name:</strong> Abhyam Mathur</div>
	<div class="chip"><strong>Roll No:</strong> R2142230904</div>
	<div class="chip"><strong>SAP ID:</strong> 500121822</div>
	<div class="chip"><strong>University:</strong> UPES</div>
</div>

## Experiments

<div class="grid">
	<article class="card">
		<h3>Experiment 1: VM vs Container</h3>
		<p>Comparative setup and behavior analysis between virtual machines and containers.</p>
		<a class="button" href="Ex1/exp1.html">Open Experiment 1</a>
	</article>

	<article class="card">
		<h3>Experiment 2: Docker Installation and Basics</h3>
		<p>Docker setup, image pull/run lifecycle, and basic command workflow.</p>
		<a class="button" href="Ex2/Ex2.html">Open Experiment 2</a>
	</article>

	<article class="card">
		<h3>Experiment 3: NGINX Base Image Comparison</h3>
		<p>Deployment and layer-level comparison across official, Ubuntu, and Alpine images.</p>
		<a class="button" href="exp3/intro.html">Open Experiment 3</a>
	</article>

	<article class="card">
		<h3>Experiment 4: Docker Essentials</h3>
		<p>Dockerfile workflow, optimization, and core containerization practices.</p>
		<a class="button" href="exp4/experiment-4-docker-essentials.html">Open Experiment 4</a>
	</article>

	<article class="card">
		<h3>Experiment 5: Volumes, Env, Monitoring, Networks</h3>
		<p>Persistence, configuration management, observability, and networking fundamentals.</p>
		<a class="button" href="exp5/intro.html">Open Experiment 5</a>
	</article>

	<article class="card">
		<h3>Experiment 6: Docker Run vs Compose</h3>
		<p>Imperative and declarative approaches for single and multi-container deployments.</p>
		<a class="button" href="exp6/Experiment6_Docker_Compose_Mayank.html">Open Experiment 6</a>
	</article>

	<article class="card">
		<h3>Experiment 7: CI/CD with Jenkins</h3>
		<p>GitHub webhook-driven build and Docker image publishing pipeline.</p>
		<a class="button" href="exp7/Lab_7_CICD_Jenkins.html">Open Experiment 7</a>
	</article>

	<article class="card">
		<h3>Experiment 9: Ansible</h3>
		<p>Agentless configuration management, playbooks, inventories, and automated server setup.</p>
		<a class="button" href="exp9/intro.html">Open Experiment 9</a>
	</article>

	<article class="card">
		<h3>Experiment 10: SonarQube</h3>
		<p>Static code analysis, quality gates, scanner setup, and CI integration.</p>
		<a class="button" href="exp10/intro.html">Open Experiment 10</a>
	</article>

	<article class="card">
		<h3>Experiment 11: Docker Stack Orchestration</h3>
		<p>Compose to Swarm progression, service scaling, and self-healing orchestration.</p>
		<a class="button" href="exp11/intro.html">Open Experiment 11</a>
	</article>

	<article class="card">
		<h3>Experiment 12: Kubernetes Draft</h3>
		<p>Core Kubernetes objects, deployments, services, scaling, and cluster basics.</p>
		<a class="button" href="exp12/intro.html">Open Experiment 12</a>
	</article>
</div>
