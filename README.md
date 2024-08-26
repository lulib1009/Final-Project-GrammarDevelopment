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

# Implementation approach/design

A grammar that can correctly parse and generate syntactic structures with different sentence types is developed for Spanish language, using XLE.
Different phenomena as mentioned above was being tried to be implemented with using the rules of LFG.

The grammar is divided into modules which are 'RULES', 'MORPHOLOGY', 'TEMPLATES', and 'LEXICON'. Such an approach allows each aspect of the grammar to be independently developed and easily progressed. For example, with templates, we can easily refer to our templates when making lexical entries, making our work easier and creating a grammar that is easier to understand.

The grammar created is a rule-based grammar, where specific and customized rules are created according to the structure of certain sentences in Spanish. Each rule is designed to handle different phenomena in the chosen language such as subject-verb agreement, yes-no questions, imperatives etc. For instance the rule "Simp --> e:  {(^ SUBJ PRED) = 'pro' (^ SUBJ PERS) = 2 | (^ SUBJ PRED) = 'pro'(^ SUBJ PERS) = 1};VP." provides that the subject's predicate must be a pronoun, either second or first person, and a verb phrase must follow the subject in order to an imperative sentence to be parsed.

The use of OT Marks:

The use of OT Marks is so important for the grammar to be able to rank and specify th differences amoong the competing syntactic structures. OT marks apply to specific structures and are used to indicate what is preferred or not preferred in those structures. For example, the OT mark '@(OT-MARK Punct)' is applied since punctuation has the potential to affect syntactic structure, semantics, prosody and, of course, meaning, it is important to specify what is preferred in terms of sytantic structure, as mentioned earlier, using OT marks. By adding a punctuation constraint to the XLE, it shows how punctuation is to be handled and ensures that it is compatible with the grammatical rules being encoded.


# Files
