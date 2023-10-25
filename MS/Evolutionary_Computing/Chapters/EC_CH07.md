# Parameters and Parameter Tuning

- [[History]]
- Taxonomy
	![[Parameter_taxonomy_img.png]]
- [[Parameter Tuning vs Parameter Control]]
- [[Testing]]
- [[Effort]]
- Recommendation
	- DO TUNE your evolutionary algorithm
	- Think of the “magic constants” (i.e., parameters hidden in the code)
	- Decide: speed or solution quality?
	- Decide: specialist of generalist EA?
	- Measure and report tuning effort
- [[Examples]]
- [[Future]]

# Important Points on Parameter Tuning and Control

- **Parameters vs. Parameter Values**: It's crucial to distinguish between the parameters themselves (which define what aspects of the algorithm can be adjusted) and the specific values those parameters can take.
- **Some Parameters Matter More Than Others**: Not all parameters have the same impact on the performance of the algorithm. Some can significantly affect the results, while others might have minimal or no impact.
- **Tune the Right Parameters**: To increase performance, focus on tuning the parameters that matter most. This requires understanding of both the algorithm and the problem at hand.
- **Decide What You're Tuning For**: Different performance measures might require different parameter settings. For example, if you're tuning for speed, you might prioritize different parameters than if you're tuning for solution quality. Common performance measures include Average Evaluation Steps (AES) for speed, Mean Best Fitness (MBF) for quality, and Success Rate (SR) for reliability.
- **Any Tuner is Better Than No Tuner**: Even a basic tuner can often improve performance compared to not tuning at all. As you gain experience with tuning, you can start to use more advanced methods.