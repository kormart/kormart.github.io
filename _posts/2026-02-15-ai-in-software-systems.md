---
layout: post
title: "🇸🇪 AI i mjukvarusystem / 🇬🇧 AI in Software Systems"
date: 2026-02-15 12:00:00 -0000
categories: coding ai
---

There is a version in English below.

Det är allt mer snack om att 24e november 2025 kommer räknas som ett historiskt datum. Det var då Anthropic släppte AI-modellen Opus 4.5. Och när den används tillsammans med agenten Claude Code passerades en gräns, åtminstone för mjukvaruutveckling, där kvaliten blev påtagligt förbättrad. 

Men utveckling slutar inte där. Hittills hjälper AI-agenter till med generering av källkod som därefter granskas av människor innan den färdiga mjukvaran driftsätts. Det har även forskats mycket inom neurosymboliska metoder, där fokus fortfarande är på källkodsnivå. Men kan AI-systemen få ännu mer direkt påverkan på ett mjukvarusystem? Två projekt tar olika vägar framåt.

Nyckeln i båda projekten är att se bortom källkoden och in i själva kodexekveringen (på engelska runtime), den dynamiska tillståndsmaskin där värden beräknas och lagras och kommunikation sker till och från externa system. Källkoden är så klart instruktionen för denna exekvering. Men ofta finns icke-determinism i externa system och tidsutvecklingen av exekveringens tillstånd blir mycket komplex. Människor som programmerar försöker ibland simulera detta genom att tänka på hur variablers värden ändras och därmed upptäcka problem. Ibland används avlusare (debuggers) som ger en direkt inblick i tillstånden i kodexekveringen. Men människor har begränsningar i skalan av tillstånd som kan hållas i tanken. 

Så hur kan en AI-agent får tillgång och påverka kodexekveringen? Ett angreppssätt (som används av startupbolget Symbolica i deras agentramverk Agentica) är att låta AI-genererade kod-fragment inkluderas i en pågående exekveringsmiljö. Man kan säga att nya objekt och funktioner (instanser därav) sys ihop med de redan befintliga, så att funktionalitet och andra egenskaper kan ändras dynamiskt. En utmaning är att få typer och funktionssignaturer att passa ihop. Man lutar sig mot kända metoder inom typteori och funktionell programmering (kategoriteori). En fördel med detta angreppssätt är att det ökar effektivitet och precision att lyfta ut delar av lösningen från den generativa AI-modellen.    

Ett annat angreppssätt är att modellera (representera) hela exekveringsmiljön i AI-modellens inre rymd, den latenta rymden. Ett projekt hos Metas FAIR-grupp, Code World Model (CWM), samlar ihop stora mängder data från tidsutvecklingar (spår) av kodexekvering, och gör förstärkningsinlärning på detta. Syftet just nu är att generera bättre källkod. Men man kan tänka sig i en förlängning att representationen av exekveringen blir tillräckligt bra så att man inte behöver köra källkoden. En möjlig fördel med detta angreppssätt är att det liknar andra domäners World Model-skapande, tex de för robotik och industriella system. Uppenbara nackdelar (ungefär samma som det välkända problemet med AI-modellers oförmåga att räkna med stora tal) är dålig skalbarhet och effektivitet.

Denna utveckling skapar möjligheter för mera autonomi och själv-förändrande (i bästa fall själv-förbättrande) egenskaper hos system. AI-agenter kan bli närmare integrerade i produkter och processer. Det uppstår så klart också många frågor. Förutom att kvalitet och tillförlitlighet måste bli tillräckligt bra, hur kan människor kontrollera, styra och få förklarbarhet i dessa system?

Och varför är Claude Code med Opus 4.5/4.6 så mycket bättre än andra kod-agenter? Förmodligen har Anthropic ansträngt sig mer än andra för att AI-modellen ska vara bra på just källkod, tex genom post-träning-steg där förstärkningsinlärning (Reinforcement Learning) används på testfrågor där man kan skapa verifierbara belöningssignaler (Verifiable Rewards).


## Reading list

* Semianalysis, [Claude Code is the inflection point](https://newsletter.semianalysis.com/p/claude-code-is-the-inflection-point)
* Steve Yegge, [The AI Vampire](https://steve-yegge.medium.com/the-ai-vampire-eda6e4f07163)
* Symbolica / Agentica, [Beyond Code Mode](https://www.symbolica.ai/agentica)
* Code World Models, Meta FAIR, [arXiv:2510.02387](https://arxiv.org/abs/2510.02387)

Version in english

There's increasing talk that November 24, 2025 will be counted as a historic date. That's when Anthropic released the AI model Opus 4.5. And when used together with the Claude Code agent, a threshold was crossed, at least for software development, where the quality became noticeably improved.

But development doesn't stop there. Until now, AI agents have helped with source code generation which is then reviewed by humans before the finished software is deployed. There has also been much research within neurosymbolic methods, where the focus is still at the source code level. But can AI systems have even more direct impact on a software system? Two projects are taking different paths forward.

The key in both projects is to look beyond the source code and into the actual code execution (runtime), the dynamic state machine where values are calculated and stored and communication occurs to and from external systems. The source code is of course the instruction for this execution. But often there is non-determinism in external systems and the time evolution of the execution's state becomes very complex. Humans who program sometimes try to simulate this by thinking about how variable values change and thereby discover problems. Sometimes debuggers are used which give direct insight into the states in code execution. But humans have limitations in the scale of states that can be held in mind.

So how can an AI agent gain access to and affect code execution? One approach (used by the startup company Symbolica in their agent framework Agentica) is to let AI-generated code fragments be included in an ongoing execution environment. You could say that new objects and functions (instances thereof) are stitched together with those already existing, so that functionality and other properties can be changed dynamically. A challenge is getting types and function signatures to fit together. They lean on known methods from type theory and functional programming (category theory). An advantage of this approach is that it increases efficiency and precision to lift out parts of the solution from the generative AI model.

Another approach is to model (represent) the entire execution environment in the AI model's inner space, the latent space. A project at Meta's FAIR group, Code World Model (CWM), collects large amounts of data from time evolutions (traces) of code execution, and performs reinforcement learning on this. The purpose right now is to generate better source code. But one could imagine in an extension that the representation of execution becomes good enough that you don't need to run the source code. A possible advantage of this approach is that it resembles other domains' World Model creation, for example those for robotics and industrial systems. Obvious disadvantages (roughly the same as the well-known problem with AI models' inability to calculate with large numbers) are poor scalability and efficiency.

This development creates opportunities for more autonomy and self-modifying (in the best case self-improving) properties in systems. AI capabilities can become more closely integrated into products and processes. Of course, many questions also arise. Besides quality and reliability needing to become good enough, how can humans control, steer and achieve explainability in these systems?

And why is Claude Code with Opus 4.5/4.6 so much better than other code agents? Presumably Anthropic has made more effort than others to make the AI model good, specifically, at source code, for example through post-training steps where Reinforcement Learning is used on test questions where you can create Verifiable Rewards (RLVR).

