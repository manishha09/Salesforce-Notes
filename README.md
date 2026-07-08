# Salesforce-Notes

Here's a practical rundown of each, with the Apex-specific gotchas that trip people up (especially coming from Java or a Node/TypeScript background).
Primitive data types
Apex primitives are Integer, Long, Double, Decimal, Boolean, String, Id, Blob, Date, Datetime, and Time. The numeric ones are worth distinguishing:

Integer — 32-bit signed (~±2.1 billion). Long — 64-bit, for anything bigger.
Decimal — arbitrary fixed precision, the correct choice for currency and anything where rounding matters. All currency/number fields from records come back as Decimal.
Double — 64-bit floating point; fine for scientific math, wrong for money.

The single biggest difference from Java: every Apex variable can be null, including Integer and Boolean. There's no unboxed primitive. An unassigned Integer i; is null, not 0. This matters constantly for null handling (below).
Also watch integer division — 5 / 2 is 2, not 2.5. Cast a operand first: 5 / (Decimal)2 or 5.0 / 2.
apexInteger count;              // null, not 0
Decimal price = 19.99;
Boolean isActive;          // null, not false
Id recordId = '001xx000003DGb2AAG';
