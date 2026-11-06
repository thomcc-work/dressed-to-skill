# Check for unsupported restrictions

Use this focused check when a concrete question concerns whether a contract restricts governing requirements, supported cases, or permitted forms of explanation.
It is owned by `spec-review`; consulting it does not start a full specification-contract audit.

For requirements and implementation specs, first establish what the governing sources permit.
Only then assess what the specification's eligibility rules accept or reject.
When tracing a draft constraint to approval, apply
[decision authority](../../references/change-with-evidence.md#decision-authority).

1. **Establish authority and permitted cases.** First read the user's request, governing sources, and established product decisions, including an approved brief when one exists.
   Write down a few cases that are otherwise valid and permitted, noting which groups they belong to by origin or scope.
   For each form of explanation that the source permits, identify the least evidence that is sufficient for it.
   If eligibility differs between those groups, include otherwise-similar cases from both.
   Looking only at the more restricted group cannot establish what the other group is allowed to do.
   Keep uncertainty visible: neither a draft definition nor a label citing a source clause can grant itself authority.
2. **Trace eligibility restrictions.** Check definitions, examples, and acceptance criteria for eligibility rules, rejection conditions, and evidence burdens.
   For each stronger condition, identify its authoritative source and explain why it is needed to enforce that source.
   Apply the source's rule to the same groups, under the same conditions, and at the same stage.
   For example, do not silently apply a restriction on new forms to inherited forms, or turn a condition for final adoption into a condition for pre-review.
3. **Check permitted forms of explanation.** Compare draft words such as “explained,” “justified,” “supported,” and “valid” with the forms of explanation and sufficient evidence recorded in step 1.
   For each form the source permits, establish observable evidence sufficient for it.
   Do not assume that every form needs a derivation from a rule or the same kind of justification.
4. **Compare plausible readings.** If an eligibility term in the draft has two plausible meanings, apply both meanings to the same otherwise-valid case permitted by the governing source.
   If one meaning admits the case and the other rejects it, that is a material ambiguity even if the draft contains no direct contradiction.
   When the source settles the case, ask for wording and acceptance evidence that preserve the source's permission.
   When it does not, name the product decision needed before approval.
   Do not choose the stricter meaning just because it seems “safer.”
5. **Trace the acceptance decision.** Follow each case to the specification's condition that rejects it or leaves acceptance unresolved.
   Flag unsupported restrictions, including those framed as safety or validation requirements, while preserving approved limits.
   If authority is missing, that limits what the review can conclude; it does not prove the restriction false.

For example, consider a stenography translator that maps key sequences to text.
Suppose its governing requirements permit entries retained from an existing dictionary even when they are not derived from a spelling rule, and explicitly count them as memorized exceptions.
Consider an otherwise-valid design that retains one exact mapping, verifies the identity of its source dictionary, and records the missing derivation from the selected rule.
Ask whether the authority requires independent evidence of conflict or irregularity, or whether the stated facts suffice to count the mapping as memorized.
If the authority settles the question, preserve its answer; if not, name the product decision needed before approval.
Do not impose an independent-evidence requirement without that authority.
Resolve the difference before approval; “justified exception” by itself does not say what qualifies.
A missing derivation from a rule is not the same as a missing explanation when the source permits memorized mappings as a form of explanation.
