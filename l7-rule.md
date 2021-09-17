---

copyright:
  years: 2017, 2019
lastupdated: "2019-07-01"

keywords: layer 7 rules

subcollection: loadbalancer-service

---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:term: .term}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:table: .aria-labeledby="caption"}
{:external: target="_blank" .external}
{:table: .aria-labeledby="caption"}
{:generic: data-hd-programlang="generic"}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}


# Layer 7 rules
{: #layer-7-rules}

Layer 7 rules define a portion of the incoming traffic that is to be matched with specific values.

* If the incoming traffic matches the specified value of a rule, then the rule evaluates to `true`.
* Layer 7 rules are always associated with a Layer 7 policy. Multiple Layer 7 rules can be associated with the same Layer 7 policy.
* If multiple rules are associated with a policy, then each rule is evaluated to be `true` or `false`.
* If all the rules that are associated to a policy evaluate to `true`, then the policy action is applied to the request. Otherwise, the load balancer evaluates the next policy.

   ![Layer 7 Add Rules](images/Layer7-AddRules.png "Layer 7 Add Rules")


Rules have types, which indicate the portion of the Layer 7 traffic to be matched with the rule.

Type      |  Field to be extracted and evaluated
----------| -----------------------
`HOST_NAME` | The hostname part of the URL (for example, `api.my_company.com`)
`FILE_TYPE` | The end of the URL, representing the file type (for example, `jpg`)
HEADER    | A field in the HTTP header
COOKIE    | A named cookie in the HTTP header
PATH      | The part of the URL that follows the hostname (for example, `/index.html`)

![Layer 7 Rules](images/Layer7-Rules.png "Layer 7 Rules")


Rules also have a comparison type, which indicates how they are to be evaluated. Rules can have following comparison types:

Comparison Type |  Type of evaluation
----------------|---------------------
`REGEX`           |  Match the extracted field (for example, `hostname`) with the supplied regular expression
`STARTS_WITH`     |  Verify whether the extracted field starts with the supplied string
`ENDS_WITH`       |  Verify whether the extracted field ends with the supplied string
`CONTAINS`        |  Verify whether the extracted field contains the supplied string
`EQUAL_TO`        |  Verify whether the extracted field is identical to the supplied string

Not all rule types support all comparison types. For example, if you are using `FILE_TYPE`, it is best to use comparison types `REGEX` and `ENDS_WITH`.
{: tip}

## Layer 7 rule properties
{: #layer-7-rule-props}

Property  | Description
------------- | -------------
Type | Specifies the type of rule. Rule types can be `HOST_NAME`, `FILE_TYPE`, `HEADER`, `COOKIE`, or `PATH`.
Comparison Type | Comparison types are used in association with the rule type, key, and value to define a rule and classify traffic. Comparison types can be: `REGEX`, `STARTS_WITH`, `ENDS_WITH`, `CONTAINS`, and `EQUAL_TO`.
Key | The description key for the rule types `HEADER` and `COOKIE`.
Value |  For the rule types `HEADER` and `COOKIE`, the value is compared against the key.
Invert | If you set the value to 1, the value of this L7 rule comparison is set to `true` whenever the specified rule is not matched.
Layer 7 Policy ID | The unique identifier of the policy to which the rules are attached.
