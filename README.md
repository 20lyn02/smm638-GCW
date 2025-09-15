<h1>Network Analytics for R&D Efficiency: Silicon Semiconductor</h1>

<h2>Description</h2>
This project models how knowledge-exchange network structure influences R&D project outcomes at a semiconductor firm (“Silicon”). Using team–employee affiliations, project outcomes, and a knowledge-sharing network from consecutive quarters, we quantify how team-level connectivity relates to <i>novelty</i>, <i>duration</i>, and <i>technical success</i>—and translate the results into recommendations for improving R&D efficiency. :contentReference[oaicite:0]{index=0}
<br />

<h2>Languages and Utilities Used</h2>

- <b>R</b> (ggplot2, gridExtra, MASS, car, glmnet)  
- <b>Statistical Modelling</b> (OLS, Stepwise with AIC, Logistic Regression)  
- <b>Network Metrics</b> (clustering coefficient, Burt’s constraint, node betweenness centrality, node degree) :contentReference[oaicite:1]{index=1}


<h2>Methodology</h2>

1. <b>Data Assembly</b>  
   - Merged team–employee affiliations with a Q4’23 knowledge-exchange network; aggregated individual network metrics to the team level.  
   - Joined team-level metrics to Q1’24 project outcomes (novelty score, duration in days, technical success). :contentReference[oaicite:2]{index=2}

2. <b>Exploration & Collinearity Checks</b>  
   - Visual EDA of novelty vs. duration (sized by team size; coloured by success).  
   - Variance inflation factors (VIF) identified strong collinearity among network metrics—especially clustering coefficient and Burt’s constraint—so models were specified and compared with careful variable selection. :contentReference[oaicite:3]{index=3}

3. <b>Regression for Novelty & Duration</b>  
   - OLS with stepwise (AIC) selection across alternative specifications (dropping collinear terms).  
   - Residual diagnostics to check linearity, leverage/outliers, and approximate normality. :contentReference[oaicite:4]{index=4}

4. <b>Logistic Regression for Technical Success</b>  
   - Binary outcome (success vs. abandoned); compared network metrics and included duration where relevant.  
   - Visualised predicted success vs. key network drivers with confidence bands. :contentReference[oaicite:5]{index=5}


<h2>Findings</h2>

- <b>Project Novelty (OLS):</b>  
  - Higher <i>node betweenness centrality (NBC)</i> → higher novelty (positive, significant).  
  - Higher <i>clustering</i> and <i>Burt’s constraint</i> → lower novelty (negative, significant).  
  - Interpretation: teams bridging disparate subgroups (low constraint, low clustering, higher NBC) produce more novel outcomes. :contentReference[oaicite:6]{index=6}

- <b>Project Duration (OLS):</b>  
  - Higher <i>NBC</i> → longer projects (positive, significant).  
  - Higher <i>clustering</i> and <i>Burt’s constraint</i> → shorter projects (negative, significant).  
  - Trade-off: structures that boost novelty tend to extend timelines; cohesive structures speed delivery. :contentReference[oaicite:7]{index=7}

- <b>Technical Success (Logit):</b>  
  - Higher <i>clustering</i> and <i>Burt’s constraint</i> → higher probability of success (positive, significant).  
  - Higher <i>NBC</i> → lower probability of success (negative, significant).  
  - Longer <i>duration</i> → lower success likelihood. :contentReference[oaicite:8]{index=8}

- <b>Implication:</b> There is a structural tension: brokers/bridges (higher NBC) help <i>innovation</i> but may hurt <i>speed</i> and <i>success rates</i>. Cohesive networks aid execution but can dampen novelty. Balancing “bridging” for ideas with “bonding” for delivery is key. :contentReference[oaicite:9]{index=9}
