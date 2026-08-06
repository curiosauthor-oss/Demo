# Customer Billing Refund and Service Credit Policy

Policy reference: CBRP-2026-01
Effective date: 1 August 2026
Owner: Customer Billing Operations

## Purpose

This policy defines when a customer billing refund can proceed automatically and when a Customer Service Representative must review the request.

## Required information

A refund request must include:

- a valid invoice number;
- the requested refund amount;
- the reason for the refund; and
- enough information to match the request to the customer account and invoice.

If any required information is missing, request that information from the customer before continuing.

## Eligible refund reasons

A refund may be considered for one of the following reasons:

- duplicate charge;
- incorrect amount charged;
- charge raised after a confirmed cancellation; or
- payment collected for a service that was not delivered.

Requests for goodwill compensation, consequential loss, or an unrelated commercial dispute are not eligible for automatic refund processing and require CSR review.

## Invoice and account validation

Before applying the monetary threshold, confirm from the billing system that:

- the invoice exists and belongs to the customer account;
- the invoice has been paid;
- the customer account is active;
- the requested amount does not exceed the refundable invoice balance; and
- the request was made within 30 calendar days of the invoice date.

If the invoice cannot be validated, request corrected invoice information. If the invoice is unpaid, the account is inactive, the amount exceeds the refundable balance, or the request is outside 30 days, route the request for CSR review.

## Decision rules

Apply these rules in order:

1. If required information is missing, return `REQUEST_INFORMATION`.
2. If the invoice number cannot be matched, return `REQUEST_INFORMATION`.
3. If the request fails an account, invoice, balance, time-limit, or eligible-reason check, return `CSR_REVIEW_REQUIRED`.
4. If all eligibility checks pass and the requested amount is 100 USD or less, return `ELIGIBLE_FOR_AUTOMATED_REFUND`.
5. If all eligibility checks pass and the requested amount is greater than 100 USD, return `CSR_REVIEW_REQUIRED`.

Exactly 100 USD is within the automated-refund limit. Any amount above 100 USD requires CSR review.

## Expected outcome

For each evaluation, provide:

- the decision;
- a concise explanation;
- the invoice and amount evaluated;
- the policy reference `CBRP-2026-01`;
- whether CSR review is required; and
- the next permitted action.

An eligibility decision confirms only that the request may proceed to the appropriate refund-processing action. It is not evidence that funds have been returned to the customer.
