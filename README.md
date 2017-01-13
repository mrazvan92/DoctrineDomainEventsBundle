# DoctrineDomainEventsBundel

With this Bundle we can send all the events which were generated by entities at SimpleBus

#Install

- SimpleBus/SymfonyBridge: http://simplebus.github.io/SymfonyBridge/
- You need to enable the DoctrineDomainEvents in your project


```
 $bundles = [
    ...
    new MR\DoctrineDomainEventsBundle\DoctrineDomainEventsBundle(),
    ...
 ];
```

#Usage

- after doctrine flush this event will be sent at rabbit queue

```
use SimpleBus\Message\Recorder\{PrivateMessageRecorderCapabilities, ContainsRecordedMessages};

class EntityName implements ContainsRecordedMessages
{
    use PrivateMessageRecorderCapabilities;

    public function __construct()
    {
        $this->record(
            new EventClass(
               'value1',
               'value2'
            )
        );
    }
}

```