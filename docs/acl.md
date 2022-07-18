- access restriction mechanish
- access to each page defined in ACL resource
## ACL check ,Implement _isAllowed() method

|  class | method   
|---|---|
| Generic backend controller  |  Determines whether current user is allowed to access Action <br/> Check current user permission on resource and privilege |
| Magento\Backend\App\AbstractAction  | _isAllowed (resource,privilege=null) |

```
protected function _isAllowed()
    {
        return $this->_authorization->isAllowed(static::ADMIN_RESOURCE); 
    }
```    

## reference
![abstractAction](https://i.ibb.co/gy0LFMP/Abstract-Action.png)

