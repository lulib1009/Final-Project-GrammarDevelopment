# grammar_dev

# Overview



# Why we choose these phenomena
 1. Verbal complexes: verbs have to agree with the noun in number and gender. Also implemented present and past.
 2. Determiner/Adjective/noun agreement in gender and number, and subject/verb agreement.
 3. internal NP structure. Different positioning of the adjectives and adverbs since Spanish is a rather flexible language in terms of word order.
 4. Dilect differences: Argentinian dialect vs. Castillian Spanish: differences between in verbs conjugation and pronoun usage.
 5. Subordinate clauses with 'que' .
 6. Negation with 'no'
 7. Imperatives: including 1st person plural imperatives.
 8. Yes/no questions: in argentinian dialect and castillian spanish

Clarification: In Spanish all questions and exclamatory senteces use their respective punctuation marks at beggining of the sentences and at the end. However, **the XLE or lfg or i dont what it is exactly** does not have the opening question mark **¿** and the opening exclamation mark **¡**. Therefore, we decided to parse the senteces without the questions mark and write this disclamer announcing that they actually exist and should be there in the senteces, we even put it in the grammar in the punctuation section even though they are not used. 

More so, several words in Spanish hace an orthographic accent, but the XLE does not recognize them properly in some occassions. So, what we decided to do is to keep them in the cases in which the XLE recognized them and to take them out when they were causing trouble. Nevertheless, there are several verbs in Spanish that need that accent in order to be differentiated in mood and/or tense. For example: *Comé* and *Confiá* are verbs that need the final accent in order to be in imperative mood in the presente tende, otherwise *Come* and *Confia* would still be in the present tense, but the mood changes into indicative. A second example is *Corrió*, in which luckily the accent is recognized in the XLE, that is the past form of the verb *correr* in the 3rd person singular, and this verbs form needs the accent to be orthographically correct becuase *corrio* without the accent does not exist. Finally, the accents in *Tenés* and *Querés* is necessary in the Argentinian dialect's way of conjugating the verbs in the 2nd person singular, just like the accent in *Tenéis* for the 2nd person plural in Castillian Spanish. (In case, of receiving an error messgae when parsing these senteces take into account that the mistake could be the accen recognition, also, if you make a mistake when writing the accents you will have to rewrite the senteces again because the XLE does not catch it correctly.)



# Implementation approach/design

A grammar that can correctly parse and generate syntactic structures with different sentence types is developed for Spanish language, using XLE.
Different phenomena as mentioned above was being tried to be implemented with using the rules of LFG.

The grammar is divided into modules which are 'RULES', 'MORPHOLOGY', 'TEMPLATES', and 'LEXICON'. Such an approach allows each aspect of the grammar to be independently developed and easily progressed. For example, with templates, we can easily refer to our templates when making lexical entries, making our work easier and creating a grammar that is easier to understand.

The grammar created is a rule-based grammar, where specific and customized rules are created according to the structure of certain sentences in Spanish. Each rule is designed to handle different phenomena in the chosen language such as subject-verb agreement, yes-no questions, imperatives etc. For instance the rule "Simp --> e:  {(^ SUBJ PRED) = 'pro' (^ SUBJ PERS) = 2 | (^ SUBJ PRED) = 'pro'(^ SUBJ PERS) = 1};VP." provides that the subject's predicate must be a pronoun, either second or first person, and a verb phrase must follow the subject in order to an imperative sentence to be parsed.

The use of OT Marks:

The use of OT Marks is so important for the grammar to be able to rank and specify th differences amoong the competing syntactic structures. OT marks apply to specific structures and are used to indicate what is preferred or not preferred in those structures. For example, the OT mark '@(OT-MARK Punct)' is applied since punctuation has the potential to affect syntactic structure, semantics, prosody and, of course, meaning, it is important to specify what is preferred in terms of sytantic structure, as mentioned earlier, using OT marks. By adding a punctuation constraint to the XLE, it shows how punctuation is to be handled and ensures that it is compatible with the grammatical rules being encoded.


# Files
