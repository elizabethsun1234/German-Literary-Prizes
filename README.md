DEUTSCHER BUCHPREIS DATASET

Motivation: 

Since its inception in 2005, the Deutscher Buchpreis has garnered a reputation in Germany comparable to the English-language Booker Prize and the French-language Prix Goncourt prize. Every year, a winner is selected amongst 6 shortlisted texts, which are chosen amongst 20 long listed texts. In this topic modeling exercise, I was curious about whether there was an evolution in the major themes across the shortlisted and winning texts. 

Dataset
	Going through the pages of deutscher-buchpreis.de, I manually copied the novel blurb and jury rationale for every shortlisted and winning novel from 2005 to 2025, which amalgamated to 125 entries in total. Initially, I compiled text from only 5 years (25 total entries), but then realized that this sample size did not produce meaningful results. 


Prompt Evolution (3+ attempts) 

INITIAL PROMPT 
Please write a python script that builds a JSON or csv file from the attached .docx file that would allow me to topic model based on either novel topic or jury rationale. Note that the text is in German. In the word file, I first have a table with the title, author, publisher, year, and status (whether the text won) for novels which were shortlisted for the German-language Deutscher Buchpreis from 2018 to 2022. Underneath the table, I have listed the description and jury rationale for each shortlisted title in chronological order, also marked by year. 

Here is an example of how the .docx is structured:
</prompt>

<example>
2018
Title: Archipel
Rosa kehrt zurück nach Teneriffa, in das heruntergewirtschaftete Haus der vormals einflussreichen Bernadottes. Rosa sucht. Was, weiß sie nicht genau. Ihr Großvater Julio war Kurier im Bürgerkrieg, war Gefangener der Faschisten, er floh und kam wieder, und heute hütet er die letzte Lebenspforte der Alten von der Insel. Einer, der Privilegien nur als die der anderen kennt. „Archipel“ führt rückwärts durch Julios Jahrhundert, das der Bautes und Bernadottes, der Wieses, der Moores und González’, aber auch derer, die keine Namen haben.

Kommentar der Jury
Inger-Maria Mahlkes Roman „Archipel“ ist eine große Reise durch die Zeit und bis ans Ende Europas. Die Städte Teneriffas atmen ihren ewigen Sommer, aber zwischen all den Gerüchen und Geräuschen des Südens spürt man den Luftzug eines ganzen Jahrhunderts. Während in einem Altenheim die Menschen ihre letzten Wege gehen, versuchen es die Jungen mit neuer Hoffnung. Es ist der Zyklus des Privaten, den Inger-Maria Mahlke auf grandiose Weise mit dem Politischen verknüpft. Und so blättert man durch hundert Jahre wie durch ein Album voll schmerzhaft schöner und genauer Bilder. Sieht Abkömmlinge der spanischen Konquistadoren und majestätische Putzfrauen, Aufstieg und Abstieg, Liebe und Korruption.
</example>

<prompt>
“Archipel” is the title of the novel, the text directly underneath is the description of the novel, and the section under “Kommentar der Jury” is the jury’s rationale for either selecting the novel to be the winning text or to be shortlisted. 

 </prompt>

SECOND PROMPT WITH LARGER DATASET

<prompt>
Please write a python script that builds a JSON or csv file from the attached .docx file that would allow me to topic model based on either novel topic or jury rationale. Note that the text is in German. I have listed the description of the novel and jury rationale for each shortlisted title in chronological order from 2005 to 2015. Each year should have 6 shortlisted novels with one winning novel. The winning novel can be distinguished by its appearance as a double entry and the additional jury rationale section of “Begründung der Jury.” In contrast, novels which were shortlisted and did not win have only a jury rationale section under the heading “Kommentar der Jury.” Please compile additional information from https://www.deutscher-buchpreis.de/archiv for the author and publisher of each title. 

Here is an example of how the .docx is structured:
</prompt>

<example>
Archipel
Rosa kehrt zurück nach Teneriffa, in das heruntergewirtschaftete Haus der vormals einflussreichen Bernadottes. Rosa sucht. Was, weiß sie nicht genau. Ihr Großvater Julio war Kurier im Bürgerkrieg, war Gefangener der Faschisten, er floh und kam wieder, und heute hütet er die letzte Lebenspforte der Alten von der Insel. Einer, der Privilegien nur als die der anderen kennt. „Archipel“ führt rückwärts durch Julios Jahrhundert, das der Bautes und Bernadottes, der Wieses, der Moores und González’, aber auch derer, die keine Namen haben.

Kommentar der Jury
Inger-Maria Mahlkes Roman „Archipel“ ist eine große Reise durch die Zeit und bis ans Ende Europas. Die Städte Teneriffas atmen ihren ewigen Sommer, aber zwischen all den Gerüchen und Geräuschen des Südens spürt man den Luftzug eines ganzen Jahrhunderts. Während in einem Altenheim die Menschen ihre letzten Wege gehen, versuchen es die Jungen mit neuer Hoffnung. Es ist der Zyklus des Privaten, den Inger-Maria Mahlke auf grandiose Weise mit dem Politischen verknüpft. Und so blättert man durch hundert Jahre wie durch ein Album voll schmerzhaft schöner und genauer Bilder. Sieht Abkömmlinge der spanischen Konquistadoren und majestätische Putzfrauen, Aufstieg und Abstieg, Liebe und Korruption.
</example>

<prompt>
“Archipel” is the title of the novel, the text directly underneath is the description of the novel, and the section under “Kommentar der Jury” is the jury’s rationale for selecting the novel to for shortlist. The novel was shortlisted in 2018 because it is listed between the text “Roman des Jahres 2018” and “Roman des Jahres 2019” 


 </prompt>

<prompt>
Can you write a jupyter notebook for topic modeling (BERTopic specifically) that analyzes the description and jury rationale of novels in a csv over time? Attached is a sample of what the csv file looks like. 

I would like to analyze topic trends over time, and jury rationale trends over time. The language is in German. Please ensure no German stop words are captured. Also ensure that BERTopic uses a good German language model. 


 <prompt>

FINE-TUNING 
	-noticed inclusion of prepositions and author names
	-noticed confusion of Thomas Mann with “der Mann” (the man) 

 </prompt>
Great job! Please adjust the code so that the topic modeling does not include additional stop words such as author names (for reference, there is an author name column so you know when author names are being mentioned in the jury rationale or description; names of established philosophers (such as Goethe or Kafka) are okay ), prepositions (like "anhand"), function words (like "ausgehend"), academic discourse filler words (including, but not limited to:

<example>
hinsichtlich
bezüglich
im Hinblick auf
im Rahmen von
im Kontext von
auf Grundlage von
ausgehend von
dabei
zudem
ferner
somit
folglich
insbesondere
beispielsweise
</example>

and high-frequency academic verbs (including, but not limited to: 

<example>
darstellen
zeigen
ergeben
erfolgen
gelten
erfolgen
finden (sich)
lassen (sich) ) 
</example>


Thank you!
 </prompt>


 <prompt>

LATEST PROMPT 

Would you be able to adjust the model so that we can know if: 

-for any given year, is there a cap to the representation of a particular theme? For example, are these years where more than one text is about a topic that might be trending, or does the jury try to select a representative novel of a few major themes? 
-how might these novels be categorized in relation to some major themes in academic studies, including, but not limited to (ecology/eco-criticism, migration/diaspora, family, memory, trauma, Bildung/coming-of-age, digitalization, body/gender/sexuality, care/precarity)

I’ve also noticed that for some years in the current script, names of protagonists of novels (such as Helene) are included in the topic modeling. Could you rewrite the script so that the names of protagonists are excluded? 

Also, Thomas Mann and the German word “der Mann” might be confused with one another. Could you make sure that this confusion does not take place for novels that might have an unnamed character that is referred to as “der Mann.” 

 </prompt>


EVALUATIONS/RESULTS

Looking at Topic 2—there seems to be a period of time when what I would call anti-Heimat texts were popular. These were texts that prioritized pastoralism/a return to the old ways, which I deduced from the keywords “alte”; “provinz”; “land”; “Deutschland”; “dorf”; “reist”. 

Other popular themes include migration and exile(Topic 0) and Bildung/Recollection (Topic 3, where “abrechnung” means “reckoning”). There seems to be a feminist/emancipatory theme of Topic 6, which I could only conclude by looking at the representative novels for that topic. 

There is not much I can conclude from Jury rationale.

During a few years, Topics 0, 2, 3, and 6 were especially popular, with 3 out of 6 shortlisted books generally about those topics. This means that even if the jury attempts to select a range of themes, there are “hot topics” during certain years. 

Looking at the description theme mapping, where I compared topics to a list of academic themes I came up with, I can see that an extremely large number of texts are about memory/remembrance/the past 


Note: 

While manually scraping the description of every shortlisted novel, along with the jury rationale for their selection, I was already able to discern a few major topics. As I was copy-pasting from the deutscherbuchpreis online archive, I was surprised by the number of texts about the DDR period, showing a persistent desire to reflect on a specific period grounded in Berlin history. 

I was also reminded of the fact that themes of migration, diaspora, and exile had been foregrounded even in the very beginning. Because of my shorter existence as an academic, I held the hypothesis that after one of Germany’s famous prizes designated for only exophonic writers (the Chamisso Prize) was discontinued in 2017, migration writers would be highlighted in other high-profile outlets. This, however, seems not to be true. 


LIMITATIONS

At the moment, the data I produce through BERTopic does not necessarily reveal insights I cannot see through a quick scan of the material myself. I realize this is likely because I am not looking at a large enough dataset. 

I am also unable to meaningfully parse through the jury rationale through BERTopic. This is likely because jury rationale really can only focus on one or a combination of: theme/content, style, effect/impact, form/experimentation. 

NEXT STEPS

I would like to rethink the major themes I fed to the script, and come up with a more meaningful list of “hot topics” based either on scholarship within cultural studies, or other ossified forms of categorizations  (publishing categories).

I would like to compare the results from the Deutscher Buchpreis data with other high-profile literary prizes, including the Bachmann Preis and the Leipzig Preis. 
