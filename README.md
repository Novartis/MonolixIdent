This repository is for creating identifiability diagnostics with nonlinear mixed effect (NLME) software NONMEM and Monolix.  The diagnostics we recommend are likelihood profiles (LLPs) and likelihood waterfalls (LLWs).   For more information on LLWs and LLPs, see our [2017 ACoP Tutorial](https://insp.memberclicks.net/mcdatafiles/receiptattach/insp/12558470/8683037/2017-10-18_RaueStein_Identifiability_LLW_LLP_ACoP8_v4.pptx)

To create LLPs and LLWs in NONMEM using PsN, use the following commands
- *LLP:* llp run3.mod -clean=3 -thetas=1,2,3,4,5,6,7,8 -omegas=1,2,3
- *LLW:* parallel_retries run3.mod -degree=.5 -min_retries=100 -picky 

To create LLPs in Monolix, one can already use the [Rsmlx package](https://www.rdocumentation.org/packages/Rsmlx/versions/1.1.0/topics/confintmlx) with the code below.  
- r <- confintmlx(project    = "RsmlxDemo2.mlxtran", method     = "proflike", parameters = c("ka_pop","omega_ka")) 

However, the above code in R is not parallelized and can take a long time to run.  Also, code is not yet available for LLWs in Monolix.  This repository will ultimately contain code for generating Likelihood Profiles (LLPs) and Likelihood Waterfalls (LLWs) in Monolix using R with the MlxConnectors package for calling Monolix and the Batchtools for parallelizing runs.  
