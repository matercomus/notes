# Signal Detection Theory: A Deeper Look into Accuracy

Signal Detection Theory (SDT) is a framework for understanding perceptual decision making, particularly in the context of binary decisions. It’s a way to quantify perceptual skill and is especially relevant when the world around us is noisy and we need to distinguish the relevant from the irrelevant.

## Sensitivity: A Measure of Accuracy
![[internal_signal.png|300]] ![[internal_signal_noise.png|300]]
Sensitivity in SDT doesn’t only look at our ability to spot the relevant, but also at our ability to ignore the irrelevant. It’s a measure of how well we can distinguish signal from noise.

## Why Do We Need SDT?

Consider these real-world examples:

- **New York, 1999**: Amadou Diallo, a 22-year-old immigrant from Guinea, was shot and killed by four white police officers who fired a combined total of 41 shots. The officers claimed they misperceived Diallo’s wallet as being a gun.
- **London, 2005**: Jean Charles de Jimenez (27), a Brazilian immigrant, was shot eight times while boarding the underground at Stockwell Underground Station. The shooters were special ops police officers looking for a known terrorist who had bombed the underground the week before. The police admitted its mistake but reported that the victim resembled the terrorist.

These tragic incidents highlight the importance of perceptual skill in high-stakes situations.

## Quantifying Perceptual Skill

Imagine a task where soldiers have to push a button when detecting an unnatural source of light. You might think that if Observer A responds more often to the light than Observer B, then Observer A is the better soldier. But what if Observer A also responds more often when there’s no light? This is where SDT comes in.

Consider this data:

|           | Observer A | Observer B |
| --------- | ---------- | ---------- |
| Light ON  | 81 times   | 62 times   |
| Light OFF | 78 times   | 4 times    |

Observer A responds more often overall, but also makes more mistakes when there’s no light. SDT helps us take this into account.

## Sensitivity and Thresholds
![[Accuracy_table.png|300]] ![[dist_signal_noise.png]]
The proportions of hits, misses, false alarms and correct rejections depend on your threshold and the distance between signal and noise distributions. This distance varies among individuals and is called sensitivity.
![[Z-score.png|400]]
Sensitivity can be measured as the z-score for hits minus z-score for false alarms. For example, if P(hit)=0.66 and P(false alarm)=0.14, 
then sensitivity = z(0.66) - z(0.14).

*Note: z-scores are probabilities expressed as standard deviations*

This measure of sensitivity is not affected by your response threshold (or criterion). No matter where your threshold is, your ability to distinguish signal from noise remains the same!

In conclusion, Signal Detection Theory provides a robust framework for understanding and quantifying perceptual skill in noisy environments.