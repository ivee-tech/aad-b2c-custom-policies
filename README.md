# aad-b2c-custom-policies
Various examples of Azure AD B2C custom policies

In *TrustFrameworkBase.xml* file replace `your_app_object_id` with your Aplication Object Id and `your_app_client_id` with your Application (Client) Id:

``` xml
          <!-- BEGIN your_app -->
          <Metadata>
            <Item Key="ApplicationObjectId">your_app_object_id</Item>
            <Item Key="ClientId">your_app_client_id</Item>
          </Metadata>
          <!-- END your_app -->

```

In *TrustFrameworkExtensions.xml* file replace `ProxyIdentityExperienceFrameworkAppId` with the registered **ProxyIdentityExperienceFramework** Application Id and `IdentityExperienceFrameworkAppId` with the registered **IdentityExperienceFramework** Application Id.

``` xml
    <ClaimsProvider>
      <DisplayName>Local Account SignIn</DisplayName>
      <TechnicalProfiles>
        <TechnicalProfile Id="login-NonInteractive">
          <Metadata>
            <Item Key="client_id">ProxyIdentityExperienceFrameworkAppId</Item>
            <Item Key="IdTokenAudience">IdentityExperienceFrameworkAppId</Item>
          </Metadata>
          <InputClaims>
            <InputClaim ClaimTypeReferenceId="client_id" DefaultValue="ProxyIdentityExperienceFrameworkAppId" />
            <InputClaim ClaimTypeReferenceId="resource_id" PartnerClaimType="resource" DefaultValue="IdentityExperienceFrameworkAppId" />
          </InputClaims>
        </TechnicalProfile>
      </TechnicalProfiles>
    </ClaimsProvider>

```

In *TrustFrameworkExtensions.xml* file replace `b2c-extensions-app_app_id` with the OOTB **b2c-extensions-app** Application Id and `b2c-extensions-app_object_id` with the OOTB **b2c-extensions-app** Object Id.

``` xml
    <ClaimsProvider>
        <DisplayName>Azure Active Directory</DisplayName>
        <TechnicalProfiles>
          <TechnicalProfile Id="AAD-Common">
            <Metadata>
              <!--Insert b2c-extensions-app application ID here, for example: 11111111-1111-1111-1111-111111111111-->  
              <Item Key="ClientId">b2c-extensions-app_app_id</Item>
              <!--Insert b2c-extensions-app application ObjectId here, for example: 22222222-2222-2222-2222-222222222222-->
              <Item Key="ApplicationObjectId">b2c-extensions-app_object_id</Item>
            </Metadata>
          </TechnicalProfile>
        </TechnicalProfiles> 
      </ClaimsProvider>
```