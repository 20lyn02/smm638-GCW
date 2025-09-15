<h1>Network Analytics for R&D Efficiency: Silicon Semiconductor</h1>

<h2>Description</h2>
This project models how knowledge-exchange network structure influences R&D project outcomes at a semiconductor firm (“Silicon”). Using team–employee affiliations, a knowledge-sharing network, and project outcomes, we quantify how team-level connectivity relates to <i>novelty</i>, <i>duration</i>, and <i>technical success</i>, and translate the results into recommendations for improving R&D efficiency.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Python</b> (NetworkX)  
- <b>R</b> (ggplot2, gridExtra, MASS, car, glmnet)  
- <b>Network Analysis</b> (degree, clustering coefficient, betweenness centrality, Burt’s constraint)  
- <b>Statistical Modelling</b> (OLS regression, stepwise AIC selection, logistic regression)


<h2>Methodology</h2>

1. <b>Graph Construction (Python / NetworkX)</b>  
   - Built the knowledge-exchange graph from edge lists; cleaned and unified employee IDs.  
   - Computed node-level metrics with NetworkX:  
     - <i>degree</i>, <i>clustering</i> (`nx.clustering`), <i>betweenness</i> (`nx.betweenness_centrality`),  
     - <i>Burt’s constraint</i> / structural holes (`networkx.algorithms.structuralholes.constraint`).  
   - Aggregated node metrics to the team level (e.g., mean/median) and exported a feature table (`silicon_stat_df.csv`).

2. <b>Exploration & Collinearity Checks (R)</b>  
   - Visual EDA: novelty vs duration (point size = team size; colour = tech success).  
   - Variance inflation factors (VIF) flagged strong collinearity among some network metrics (e.g., clustering vs Burt’s constraint), so alternative specifications were compared.

3. <b>Regression for Novelty & Duration (R)</b>  
   - OLS with stepwise (AIC) selection across competing specs that drop collinear terms.  
   - Residual diagnostics: linearity, normality, leverage/outliers.

4. <b>Technical Success (Logistic Regression, R)</b>  
   - Binary outcome (success vs not).  
   - Compared models with key network metrics and duration; plotted predicted probabilities with 95% CIs.

<h2>Findings</h2>

- <b>Novelty (OLS):</b> Higher <i>betweenness</i> → higher novelty; higher <i>clustering</i> / <i>constraint</i> → lower novelty.  
- <b>Duration (OLS):</b> Higher <i>betweenness</i> → longer timelines; higher <i>clustering</i> / <i>constraint</i> → shorter timelines.  
- <b>Technical Success (Logit):</b> Higher <i>clustering</i> / <i>constraint</i> → higher success probability; higher <i>betweenness</i> and longer duration → lower success probability.  
- <b>Implication:</b> There’s a structural tension: “bridging” (betweenness) boosts innovation but can slow delivery and reduce success rates, while “bonding” (cohesion/constraint) aids execution but can dampen novelty. The optimal design balances both.
