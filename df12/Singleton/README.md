Example implementation of Singleton assuming below is starting code.

    trigger AccountTrigger on Account (before insert, before update) {
        for(Account record : Trigger.new){
            AccountFooRecordType rt = new AccountFooRecordType();
        }
    }
 

    public class AccountFooRecordType {
        public String id {get;private set;}
        public AccountFooRecordType(){
            id = Account.sObjectType.getDescribe()
                .getRecordTypeInfosByName().get('Foo').getRecordTypeId();
        }
    }
 