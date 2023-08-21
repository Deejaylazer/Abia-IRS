# Login - Direct Assessment Module test
```cypress
describe('Direct ASSESSMENT test',() =>{
  it('Login page', ()=> {
    cy.visit('https://ics3staging.abiairs.gov.ng/auth/realms/aics/protocol/openid-connect/auth?client_id=aics-frontend&redirect_uri=https%3A%2F%2Fics3staging.abiairs.gov.ng%2Fdashboard&state=e0fd4151-643f-46e5-aa6c-c06173bcd62e&response_mode=fragment&response_type=code&scope=openid&nonce=0fbc48bf-a5c9-4eb7-a25a-ca2e07329be1')
    cy.get('#username').type('****')
    cy.get('#password').type('****')
    cy.get('#kc-login').click()

    //Direct Assessment Module
    cy.visit('https://ics3staging.abiairs.gov.ng/assessments/direct-assessments?recordType=NEW')
     //   Assessment Number
     cy.get('#validationDefault01').type(1234667887)

     //   Approval Status
     cy.get('#validationDefault05').select('DISAPPROVED')

     //  Tax Year
        cy.get('#validationDefault03').select('2021')

    //       Payment status
    cy.get('#validationDefault06').select('PAID')

    cy.contains('Date Created (From)')

    // Search button
      cy.contains('SEARCH').click()

    //Create Direct Assessment
      cy.get('.float-right>.btn>span').click()
      cy.get('#taxYear').select('2021')
      //cy.contains('Mode of Assessment').select('TAX TO INCOME')
      //.contains('Is Additional Assessment?').select('YES')
      cy.get('.col-xs-12').click()
 
  })

})
```
