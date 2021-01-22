# Examples

I'm too lazy to write a bunch of these but should be fine.

### List of accounts

You could have a DilanScript file like this:

    A data storage file for my store.
    
    // DilanScript 2
    
    name: My Cool Store
    worth: 5000000
    
    accounts {
    
        Bob {
        
            balance: 50
            phone: 1234567890
            
        }
        
        Joe {
        
            balance: 100
            phone: 0987654321
            
        }
        
        Mama {
        
            balance: 500
            phone: 1112223333
            
        }
        
    }

*Remember: any text above the `// DilanScript 2` line is ignored by the API!*

And then maybe make some use of it in Java:

    // New instance of DilanScript with error handling
    DilanScript ds = null;
    
    try {
        ds = new DilanScript(new File("thatfile.ds"));
    } catch (Exception ex) {
        ex.printStackTrace();
        return;
    }
    
    // Get the global structure
    DStructure global = ds.enter();
    
    // Get the name and worth values
    String storeName = global.get("name");
    long worth = Long.parseLong(global.get("worth"));
    
    // Create a map to store account names and their balances (phone numbers are not stored for now)
    Map<String, Integer> accountBalances = new HashMap<String, Integer>();
    
    // Enter the accounts section from the DilanScript file
    DStructure accounts = global.nest("accounts");
    
    // Loop throguh all the accounts in the section
    for (String accountOwner : accounts.getNestKeys()) {
    
        // Assign their balance to their name
        accountBalances.put(accountOwner, accounts.nest(acountOwner).get("balance"));
        
    }
    
