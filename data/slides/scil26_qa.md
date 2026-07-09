## Q1. Reasons for low performance

> I had a quick question. I noticed that your baseline model that you're reporting results on is a human-constructed grammar, right?
>
> Do you have an intuition or understanding of why MaxEnt's issue, in this context, is with precision? Do you have an interpretation of that, or is there something we should think about regarding the learning process?

**My Answer**

> For the poor performance of the baseline, I can tell you exactly why it's bad.
>
> It's because two of the constraints—**no final LH/HL**, and also **no LHLs**—are too strong. They're too restrictive. Our dataset actually contains some data points that violate these two constraints.
>
> The other three constraints, like **no rise**, **no monosyllabic contour**, and **no superheavy syllable**, are perfectly fine. So it's mostly these two overly strong constraints that hurt the baseline.
>
> As for MaxEnt, I don't know why its precision is low besides the lack of the frequency. I don't have an explanation for that yet.

---

## Q2. Frequency Information

> One of your findings is that frequency information is critical for MaxEnt, but not for BUFIA.
>
> I was wondering whether you have a normative judgment about whether frequency information *should* be necessary for learning.
>
> Is it more human-like for frequency information to be required? Conversely, if you have a learning algorithm where frequency information isn't important, could that mean the algorithm has an inductive bias that's perhaps too strong to be human-like?

**Answer**

> We don't have any judgment about what implications this has for human language learning.
>
> I think that's something we could investigate in future work, perhaps using external evidence.
>
> Right now, we're simply looking at **when** frequency information is needed in a learning scheme.
>
> What we can say from these results is that if you use **categorical learning** together with a more linguistically explicit representation, then frequency information is not necessarily needed in this setting.
>
> That's the main takeaway regarding the importance of frequency.

---

## Q3. Representation Learning 

> One of your conclusions is that BUFIA-AR achieves the best performance.
>
> I was wondering if you could say a little more about the representation side.
>
> For example, if we think about a language-acquiring child, do we assume they simply begin with this type of representation? Or is the representation itself part of the learning process?
>
> If so, could you say a little about how your conclusions bear on that question?

**Answer**

> Thank you so much for the great question.
>
> So far, whether we're talking about **segment**, **feature**, or **autosegmental representations**, we can formalize all of them in a model-theoretic framework.
>
> That means each representation defines a hypothesis space with a containment relation.
>
> By searching this containment relation, we can determine whether a superfactor is banned in the language.
>
> Specifically for BUFIA and tone, we search this partial-order hypothesis space. It's similar to what Brandon just talked about with the tonal sandhi hypothesis: you start from simple structures, such as H or L, or a syllable structure, and then gradually build more complex tonal structures.
>
> The design of BUFIA is that **the user specifies the representation**.
>
> It can work with autosegmental representations, syllable structures, or, more generally, any multi-tier representation that can be formalized model-theoretically and equipped with a containment relation.
>
> So, I don't know if that fully answers your question, but the key point is that the representation itself is not learned in this process