# Order Documents Events

The buyer and supplier can both attach documents to the order or line.

| OrderDocumentEvent                 | Webhook Configuration                                         |
| ---------------------------------- | ------------------------------------------------------------- |
| `OrderDocumentsAttachedByBuyer`    | Document(s) are attached to the order or line(s) by the buyer    |
| `OrderDocumentsAttachedBySupplier` | Document(s) are attached to the order or line(s) by the supplier |

{% hint style="warning" %}
Please note that these events are not published when documents are embedded in the buyer order message and not explicitly attached.
{% endhint %}
