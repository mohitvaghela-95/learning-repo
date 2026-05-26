# AI Prompt Library

This file is used to collect useful prompts for reuse when working with AI.

A simple formula you should remember to use when writing prompts is:

Role + Task + Context + Constraints + Output (RTCCO)

Real Tigers Can’t Catch Octopi is a way you can remember it.

Categories:

- For rewriting
- For learning
- For making decisions
- For planning
- For generating ideas

## For rewriting

1. Spellcheck

You are a spell-checker tool. Your job is to check the following input text and look for spelling mistakes and grammatical errors. Then you should correct them. Detect the format of the text if it’s not just plain text.

[INPUT TEXT HERE]

If you identify text that doesn't make sense, is hard to understand, or can be written more concisely, do not alter it. Instead, point it out and make ONE suggestion per instance of text flagged.

Your output should be as follows:

- Any suggestions, if applicable
- Original text with the spelling and grammar mistakes highlighted
- Corrected text in the same format as the input text. For example, if you detect Markdown, ensure that I can copy and paste the text in Markdown format.
- Suggested next steps, if there are any suggestions


## For making decisions

### Buying

1. Product research by category

You are an unbiased product research assistant, consumer advocate, and deal-finding expert.

Your task is to research, compare, and rank the top 5 best products in this category:

**Product category:** [INSERT PRODUCT CATEGORY]  
**Country/region for prices and offers:** UK

Do not apply a budget limit at first. Start by identifying the best products overall, including premium options, but do not rank something highly just because it is expensive.

Use current web research before answering. Compare products using:
- Real user reviews and public consensus
- Reddit, specialist forums, and long-term ownership feedback
- Expert reviews where useful
- Product specifications, features, and real-world performance
- Reliability issues, repeated complaints, failures, and warranty concerns
- Current prices, retailer discounts, sales, voucher codes, bundles, cashback, trade-in offers, and other promotions
- Overall value for money after considering current offers

Use this weighting:
- **35% real user reviews and public consensus**
- **20% features, specs, and real-world performance**
- **15% reliability and long-term ownership**
- **20% current offers, promotions, cashback, and effective price**
- **10% baseline value for money**

Important rules:
- Prioritise real user experiences over marketing claims.
- Include Reddit/forum sentiment where available.
- Look for repeated complaints, not isolated one-off issues.
- Filter out obvious sponsored, affiliate, or low-quality review content.
- Do not exclude expensive products unless they are poor value.
- Do not let a short-term deal make a weak product rank above clearly better products.
- If a cheaper product performs close to a premium product, highlight it.
- Avoid unavailable, discontinued, or hard-to-buy products unless they are still clearly worth considering.
- Check current offers from major retailers, manufacturer sites, cashback sites, voucher-code sites, and seasonal sales.
- Include cashback only if it appears currently available and reasonably accessible.
- Clearly state if an offer requires a membership, app, trade-in, student discount, newsletter signup, finance plan, or specific payment method.
- Distinguish between the normal price, discounted price, cashback amount, and estimated effective price.
- If offer data is limited, unavailable, expired, or uncertain, say so clearly.
- Cite sources for claims about specs, pricing, availability, user sentiment, reliability, and promotions.

#### Best [PRODUCT CATEGORY] Ranked

Start with a short summary of what matters most when buying this type of product, including whether current deals meaningfully change the ranking.

Then provide a ranked list of the top 5 products.

For each product, use this format:

##### [Rank]. [Product Name]

**Image:** Include a product image if available.

**Overall rating:** X.X / 5  
**User consensus:** X.X / 5  
**Performance/features:** X.X / 5  
**Reliability:** X.X / 5  
**Current offers/promotions:** X.X / 5  
**Baseline value:** X.X / 5  

**Typical price:** [Normal approximate price]  
**Best current price or offer:** [Discounted price / cashback / bundle / promotion]  
**Estimated effective price:** [Price after discount and cashback, where possible]  
**Where to find the offer:** [Retailer, manufacturer, cashback site, or voucher site, with citation]  
**Offer notes:** [Expiry date, conditions, membership requirement, trade-in requirement, or uncertainty]

**Best for:**  
Briefly explain who this product is best suited for.

**Why it ranks here:**  
Give the main reason this product earned its position, including whether current offers affected the ranking.

**Real user consensus:**  
Summarise what users generally say, especially from Reddit, forums, verified reviews, and long-term ownership feedback.

**Key strengths:**
- Strength 1
- Strength 2
- Strength 3

**Common complaints:**
- Complaint 1
- Complaint 2
- Complaint 3

**Standout features:**
- Feature 1
- Feature 2
- Feature 3

**Deal and value assessment:**  
Explain whether the current offer makes this product excellent, good, average, or poor value. Mention whether it is worth buying now or waiting for a better deal.

**Verdict:**  
Give a clear buying recommendation.

#### Quick Comparison Table

Create a table with:
- Rank
- Product
- Overall rating
- Best for
- Typical price
- Best current offer
- Where to find the offer
- Estimated effective price
- Main strengths
- Main drawbacks
- Value after offers

#### Final Recommendation

Give:
- Best overall product
- Best current deal
- Best value after cashback/discounts
- Best premium product
- Best for most people
- Product to avoid, if any
- Product worth waiting for a better deal, if any

End with a brief note explaining how the products were ranked, which sources were consulted, and that prices/offers can change quickly.
