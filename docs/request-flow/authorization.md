### Magento 2 authorization system:

1. `acl.xml` is declaring resources used for backend actions protection and web API.
2. Resulting merged `acl.xml` is used to build 2 identical ACL trees for managing permissions in the admin panel.
One is for the admin user role edit page, another is on web API integration edit page
3. Permissions are checked in `\Magento\Backend\App\AbstractAction::_isAllowed` when accessing admin panel pages  (this method is almost always overridden in child controllers to perform check against custom resource).
4.  During web API calls processing this check is done by framework based on `resources` node declared in webapi.xml
5. To check if current user (admin or web API) has permission to access particular resource declared in `acl.xml`, 
6. just use `\Magento\Framework\AuthorizationInterface::isAllowed($resource)`. User context is identified automatically in this case
