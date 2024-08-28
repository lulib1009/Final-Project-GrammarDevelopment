   # Grammar Development Final Project
   ### Spanish Grammar 
   ### SoSe 2024 
   ### Nurten Atıcı , Buket Sak, Ludmila Bajuk

# Overview
When creating a grammar for the XLE parser, it was necessary to take into account a number of linguistic complications that are specific to the Spanish language. In order to ensure accurate parsing and the creation of various sentence kinds that accurately reflect the subtleties of Spanish, this endeavor required the precise implementation of rules and structures. The study concentrated on a number of significant linguistic phenomena, each of which presented particular difficulties and called for specially designed XLE framework solutions.


# Why we choose these phenomena

 **1. Verbal complexes:** Verbs have to agree with the noun in number and gender. We implemented Present Simple and Past Perfect (*Pasado Perfecto*, which is not like Past Perfect in English, it is more like Simple Past) in Spanish, even though there are more than 15 verb tenses. Verbs are very complicated in Spanish, as we mentioned, they have different conjugations for tenses, mood, and number. This complexity was one of the reasons that we chose different verbs with different sentences. The aim was to make XLE recognize the difference and to be able to parse the sentences with the correct verb form in every way. For instance, the verb *Vamos* is the first person plural form for the verb 'Let's go', and in most languages, the base of the verb (*ir*) is usually the same but you add a suffix to conjugate it in terms of number. However, in Spanish verbs undergo a very intense inflection. Verbs also change greatly when their mood change, they can be indicative, imperative and subjunctive, and we only implemented indicative, for almost all of our senteces; and imperative, for imperative senteces that denote orders or commands. 
 
 **2. Determiner/Adjective/noun agreement in gender and number, and subject/verb agreement:** The Spanish language requires determiners, adjectives and nouns to agree in both gender and number. In terms of gender agreement, we can say that determiners and adjectives must be compatible with the nouns that they modify when they femenine or masculine. For example, we have *los niños* and *las jirafas*; and *un rico alfajor* and *unas niñas*. *Los* and *las* are the definite determiners and they match with the gender of the nouns which respectively are feminine (giraffes) and masculine (boys). If they don't match with the noun, the sentence becomes unparsable. Another significant feature anout the Spanish language is the amount of different determiners that it has, in comparison to English. There are definite and indefinite determiners that have to coincide in number and gender. *Un* (singular) and *Unas* (plural) indefinite articles that denote the difference in number agreement with the noun they accompany. Regarding adjectives, in our grammar, we have different types (attributive, superlative and demonstrative) that also have to coincide in gender and number with the determiner that preceeds them in the case of *un rico alfajor* and the noun that goes after it, if it does not there is no cohesion between the constituents of the sentence.
 
 **3. Internal NP and VP structure: Different positioning of the adjectives and adverbs:** Spanish is a rather flexible language in terms of word order. In Spanish, there are lots of positions in which adverbs and adjectives can occur thanks to its flexible word order structure. For instance adjectives can be positioned before or after the noun that they modify, which is not the case in most languages. As an example, whereas the adjective *rico* comes before the noun *alfajor* in the sentence *Pedro quiere un rico alfajor.*, the attributive adjective *morada* comes after the noun *camiseta* in the sentence *Vosotros tenéis una camiseta morada.* and both sentences' word order is completely correct. More so, the adverbs' position in a sentecescan vary. For instance, an adverb can occur within the proximity of the verb (sinceits modifying it) like in the senteces *Unos niños afirmaron que las jirafas corren libremente.*, in which the adverb *libremente* appears right after the verb. However, the adverb can be positioned after the object the verb was refereing to, as in *Unas niñas aprenden español alegremente en el colegio.* where the adverb is after the non *colegio* but still modifying the way in which the students are learning, meaning the verb *aprenden*.
 
 **4. Dilect differences: Argentinian dialect (Rioplatense Spanish) vs. Castillian Spanish**: There are many differences between these two dialect, and many of the are phonetic and phonological that we cannot implement in a grammar. However, there are also many differences in vocabulary and grammar. One of the most distinctive features of Argentinian Spanish is the use of *vos* instead of *tú* for informal second person singular ("you"). This phenomenon, known as voseo, also affects verb conjugation, resulting in forms like *vos sos* (you are) instead of *tú eres* in Castillian Spanish. Along the same lines of the voseo, in the Argentinian dialect *ustedes* is used for both formal and informal second person plural, with the same verb conjugation as the thirdperson plural, like *ustedes tienen* (you have). In contrast, Spain distinguishes with *vosotros for informal secondp erson plural, using forms like *vosotros tenéis.*, however, the *ustedes* formal form is barely used in Modern Castillian Spanish. More so, the two dialects differ in vocabulary, such as *remera* and *camiseta* (t-shirt), or there are terms that are unique in the Argentinian dialect like *alfajor* which is a specific cookie eaten in Argentina. 
 
 **5. Subordinate clauses with *que*:** Subordinate clauses are very important in the Spanish language in terms of expressing dependent ideas. And the word *que* has an important role as a key marker for these clauses since it links them to the main clause. The grammar rules must ensure that the subordinate clauses are embedded to main clauses in a correct way.And indicating that the clause represented by *que* functions as a complement (COMP), within the structure of the main clause is the way it is usually done. We also made sure that the grammar is working correctly in terms of the elements within the subordinate clause are compatible with number, gender etc. and they relate to elements in the main clause correctly.
 
 **6. Negation with *no*:** In Spanish, negation can be applied with the word *no* (not) to negate the verbs. It is always placed before the verb, making sure that the negation applies directly to the verb's action. We have used the notation '(^ NEG) = +', that marks the following verb or phrase as negated. For example, in the sentence *Pedro no quiere un alfajor.*, *no* negates the following verb/verb phrase *quiere*. 
 
 **7. Imperatives:** When we come to the imperative mood, we encounter an important feature that distinguishes Spanish from other languages. In most languages, the imperative is usually used in the second person singular or second person plural. However, Spanish also uses the imperative in the first person plural *Nosotros*, which is interesting. As in the case of the verb *Hagamos* (Let's do). The verb is conjugated in the first person plural and used in the imperative mood. For this intriguing reason, we wanted to include imperatives in our project.
 
 **8. Yes/no questions:**  In the grammar, we structured the yes/no questions in Argentinian dialect and Castillian Spanish through specific syntactic markers and rules. We used an interrogative marker in our grammar to identify yes/no questions. We have written a rule as "Sint --> e: (^ SUBJ PRED)='pro'; VP." which can be interpreted as there is a subject-predicate relationship and it's constrained to be a pronoun. Also, the entry "INT * (^ STMT-TYPE) = interrogative." is very important since it indicates that when the question mark is used, the sentence is marked as interrogative. It is a very important point in terms of XLE to distinguish between yes/no questions and declarative sentences, and parse the sentences correctly.
 
Clarification: In Spanish, all questions and exclamatory sentences use their respective punctuation marks at the beginning of the sentences and at the end. However, the XLE does not have the opening question mark **¿** and the opening exclamation mark **¡**. Therefore, we decided to parse the sentences without the question mark and write this disclaimer announcing that they actually exist and should be there in the sentences, we even put it in the grammar in the punctuation section even though they are not used. 

 **9. Topic Senteces:** 

**Disclaimer:** several words in Spanish have an orthographic accent, but the XLE does not recognize them properly in some occasions. So, what we decided to do is to keep them in the cases in which the XLE recognized them and to take them out when they were causing trouble. Nevertheless, there are several verbs in Spanish that need that accent in order to be differentiated in mood and/or tense. For example: *Comé* and *Confiá* are verbs that need the final accent in order to be in an imperative mood in the present tense, otherwise *Come* and *Confia* would still be in the present tense, but the mood changes into indicative. A second example is *Corrió*, in which luckily the accent is recognized in the XLE, which is the past form of the verb *correr* in the 3rd person singular, and this verb form needs the accent to be orthographically correct becuase *corrio* without the accent does not exist. Finally, the accents in *Tenés* and *Querés* are necessary in the Argentinian dialect's way of conjugating the verbs in the 2nd person singular, just like the accent in *Tenéis* for the 2nd person plural in Castillian Spanish. (In case, of receiving an error message when parsing these sentences take into account that the mistake could be the accent recognition, also, if you make a mistake when writing the accents you will have to rewrite the sentences again because the XLE does not catch it correctly.)


# Implementation approach/design

A grammar that can correctly parse and generate syntactic structures with different sentence types is developed for Spanish language, using XLE.
Different phenomena as mentioned above was being tried to be implemented with using the rules of LFG.

The grammar is divided into modules which are 'RULES', 'MORPHOLOGY', 'TEMPLATES', and 'LEXICON'. Such an approach allows each aspect of the grammar to be independently developed and easily progressed. For example, with templates, we can easily refer to our templates when making lexical entries, making our work easier and creating a grammar that is easier to understand.

The grammar created is a rule-based grammar, where specific and customized rules are created according to the structure of certain sentences in Spanish. Each rule is designed to handle different phenomena in the chosen language such as subject-verb agreement, yes-no questions, imperatives etc. For instance the rule "Simp --> e:  {(^ SUBJ PRED) = 'pro' (^ SUBJ PERS) = 2 | (^ SUBJ PRED) = 'pro'(^ SUBJ PERS) = 1};VP." provides that the subject's predicate must be a pronoun, either second or first person, and a verb phrase must follow the subject in order to an imperative sentence to be parsed.

The use of OT Marks:

The use of OT Marks is so important for the grammar to be able to rank and specify th differences amoong the competing syntactic structures. OT marks apply to specific structures and are used to indicate what is preferred or not preferred in those structures. For example, the OT mark '@(OT-MARK Punct)' is applied since punctuation has the potential to affect syntactic structure, semantics, prosody and, of course, meaning, it is important to specify what is preferred in terms of sytantic structure, as mentioned earlier, using OT marks. By adding a punctuation constraint to the XLE, it shows how punctuation is to be handled and ensures that it is compatible with the grammatical rules being encoded.


# Files
## Individual Contributions

| Team Member           | Contributions                                             |
|-----------------------|-----------------------------------------------------------|
| Buket Sak             | Imperatives, Subordinate Sentences, Yes/no questions      |                                                       
| Nurten Atıcı            | Topic Sentences, Agreement, Internal VP and NP structure   |
| Ludmila Bajuk         | Verbal Complexes, Negation, Dialect Differences           |
