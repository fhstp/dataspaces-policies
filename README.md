# Policy Patterns for Usage Control in Data Spaces

This repository complements the paper ["Policy Patterns for Usage Control in Data Spaces"](Policy_Patterns_for_Usage_Control_in_Data_Spaces.pdf). The work aims to contribute to the further development of automated contract negotiation and data usage policies in data spaces.

Cite As:
```
Tobias Dam, Andreas Krimbacher, and Sebastian Neumaier. Policy Patterns for Usage Control in Data Spaces. In Fifth International Workshop On A Semantic Data Space For Transport @ SEMANTiCS 2023, Leipzig, Germany, September 2023.
```
```
@inproceedings{dam2023policy,
	title        = {Policy Patterns for Usage Control in Data Spaces},
	author       = {Tobias Dam and Andreas Krimbacher and Sebastian Neumaier},
	year         = 2023,
	month        = {September},
	booktitle    = {Fifth International Workshop On A Semantic Data Space For Transport @ SEMANTiCS 2023},
	address      = {Leipzig, Germany}
}
```

## Repository Contents
### *Collection of Policy Patterns in ODRL*
We have collected a set of policy patterns for usage control that are particularly relevant in the context of data spaces. These policy patterns capture common and recurring policy requirements and scenarios encountered in data sharing and governance.

* The policy patterns were classified based on their enforcement type:
   * Preventive Mechanisms are dynamic and proactive enforcement mechanisms that allow or prohibit requests for data usage, revoke access in case of policy violations, delay usage requests until obligations are fulfilled, update user or object attributes based on usage decisions, and execute actions like sending notifications to data owners.
   * Detective Mechanisms can be applied in situations where the usage control framework cannot enforce policy restrictions or prevent policy violations. Various detective mechanisms, such as auditing, logging, or user notifications, can be employed to provide evidence or indications of executed commands.
* The stakeholders involved in the implementation of each policy pattern were identified as providers, consumers, and third parties.
* For each policy pattern in the collection, the corresponding PIP and PAP/PDP is specified: the stakeholder responsible for deploying (PAP) and evaluating (PDP) the policy, and the stakeholder responsible for providing information about its fulfillment (PIP).


| Policy Pattern               | Description / Example                                             | PIP                   | PAP/PDP  | Enforcement | ODRL File                                           |
|---------------------------|-------------------------------------------------------|-----------------|-------------|--------------|------------------------------------------------------|
| Allow access              | Provider allows access to the data for a specific consumer. | Provider        | Provider    | Preventive   | [access-specific-consumer.ttl](example-policies/access-specific-consumer.ttl)                |
| Location / Regional access restriction | Consumer can access data only if located in allowed region. | Provider        | Provider    | Detective    | [regional-access-restriction.ttl](example-policies/regional-access-restriction.ttl) |
| Location / Regional storage restriction | Consumer can store data only if the storage is located in allowed region. | Consumer, Third Party | Provider    | Detective    | [regional-storage-restriction.ttl](example-policies/regional-storage-restriction.ttl) |
| Time restriction          | Consumer can access data only in pre-defined time period. | Provider        | Provider    | Preventive   | [time-restriction.ttl](example-policies/time-restriction.ttl)                                        |
| Access count               | Consumer can access the data a fixed number of times. | Provider        | Provider    | Preventive   | [access-count-restriction.ttl](example-policies/access-count-restriction.ttl)                  |
| Rate limit                 | Consumer can access the data only a limited number of times within a period. | Provider        | Provider    | Preventive   | [rate-limiting.ttl](example-policies/rate-limiting.ttl)                                        |
| Concurrent active connections | The number of concurrent connections to retrieve the data is limited. | Provider        | Provider    | Preventive   | [concurrent-active-connections.ttl](example-policies/concurrent-active-connections.ttl)                                        |
| Amount of data             | The amount of data that can be transferred/streamed is limited. | Provider        | Provider    | Preventive   | [amount-of-data.ttl](example-policies/amount-of-data.ttl)                                    |
| Processing power           | The processing power to prepare/provide the data is limited. | Provider        | Provider    | Preventive   | [processing-power.ttl](example-policies/processing-power.ttl)                     |
| Bandwidth                  | The bandwidth to transfer/stream the data is limited. | Provider, Third Party | Provider    | Preventive   | [bandwidth.ttl](example-policies/bandwidth.ttl)             |
| Billing / Credit points    | The consumer will be charged for the data accesses. | Provider        | Provider    | Preventive   | [billing.ttl](example-policies/billing.ttl)                  |
| Data quality               | The consumer demands certain data quality standards, e.g., schema conformance, data consistency, etc. | Consumer        | Consumer    | Detective    | [data-quality.ttl](example-policies/data-quality.ttl)                                                    |
| Deletion                   | Consumer is required to delete data after a specific period. | Consumer, Third Party | Provider    | Detective    | [deletion-requirement.ttl](example-policies/deletion-requirement.ttl)                       |
| Purpose / Application      | Consumer is restricted to use data for a specific purpose only. | Consumer, Third Party | Provider    | Detective    | [purpose.ttl](example-policies/purpose.ttl)                                        |
| Provable attribute         | Provider demands a certificate/guarantee, e.g., of membership. | Provider, Third Party | Provider    | Preventive   | [provable-attributes.ttl](example-policies/provable-attributes.ttl)                      |
| Encryption by consumer     | Provider demands the consumer to store data encrypted. | Consumer        | Provider    | Detective    | [encryption-by-consumer.ttl](example-policies/encryption-by-consumer.ttl)                      |
| Encryption by provider     | Consumer demands the provider to transfer data encrypted. | Consumer        | Consumer    | Preventive   | [encryption-by-provider.ttl](example-policies/encryption-by-provider.ttl)                                                    |
| Aggregation                | Provider demands the consumer to aggregate data before processing. | Consumer        | Provider    | Detective    | [aggregation.ttl](example-policies/aggregation.ttl)                                      |
| Anonymization              | Provider demands the consumer to anonymize data before processing. | Consumer        | Provider    | Detective    | [anonymization.ttl](example-policies/anonymization.ttl)                       |
| Activity logging           | Provider demands shared activity logging of the data processing. | Consumer        | Provider    | Detective    | [activity-logging.ttl](example-policies/activity-logging.ttl)                       |
| Delegation of permission   | Provider demands attaching a certain policy when distributing the data. | Consumer        | Provider    | Detective    | [delegation.ttl](example-policies/delegation.ttl)                  |
| Up-to-dateness             | Consumer demands that the data is updated with a specified frequency. | Consumer        | Provider    | Detective    |                  [up-to-dateness.ttl](example-policies/up-to-dateness.ttl)                    |

### *ODRL Profile*
* https://w3id.org/dataspaces-policies

This ODRL Profile proposes an extensions to the ODRL vocabulary to accommodate the representation of data space-specific policies. The extension includes additional actions and operands that enhance the expressiveness of the ODRL vocabulary.

## Contributions and Feedback
Contributions to this repository are highly appreciated. If you have additional policy patterns, improvements or corrections to the existing patterns, or suggestions for enhancing the ODRL profile, please follow these steps:

1. Fork the repository.
2. Create a new branch for your contribution: `git checkout -b new-contribution`.
3. Make the necessary changes or additions.
4. Commit your changes: `git commit -am 'Add new contribution'`.
5. Push the changes to your fork: `git push origin new-contribution`.
6. Submit a pull request detailing your changes and their significance.

For any questions or feedback related to this repository or the research paper, please reach out to the authors:

* Tobias Dam: tobias.dam@fhstp.ac.at
* Sebastian Neumaier: sebastian.neumaier@fhstp.ac.at
* Andreas Krimbacher: andreas.krimbacher@nexyo.io

## License
This repository is licensed under the [GNU General Public License v3.0](LICENSE).

