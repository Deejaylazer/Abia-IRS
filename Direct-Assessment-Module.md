# Login - Direct Assessment Module test
```cypress
describe('Direct ASSESSMENT test',() =>{
  describe('Login Page', () => {
  beforeEach(() => {
    cy.visit('https://ics3staging.abiairs.gov.ng/auth/realms/aics/protocol/openid-connect/auth?client_id=aics-frontend&redirect_uri=https%3A%2F%2Fics3staging.abiairs.gov.ng%2Fdashboard&state=e0fd4151-643f-46e5-aa6c-c06173bcd62e&response_mode=fragment&response_type=code&scope=openid&nonce=0fbc48bf-a5c9-4eb7-a25a-ca2e07329be1'); 
  });

  it('should display the login form', () => {
    cy.get('form').should('be.visible');
    cy.get('input[name="username"]').should('be.visible');
    cy.get('input[name="password"]').should('be.visible');
    cy.get('#kc-login').should('be.visible');
	 cy.get('.checkbox>label').should('be.visible')
	 cy.contains('Register').should('be.visible') //Don’t have an account?
  });

  it('should navigate to password reset page on clicking reset link', () => {
    cy.contains('Forgot Password?').click() 
    cy.url().should('include', '/password-reset') //  navigates to '/password-reset' page
  })

//   it('should display an error message for invalid login', () => {
//     cy.get('input[name="username"]').type('invalidUsername');
//     cy.get('input[name="password"]').type('invalidPassword');
//     cy.get('button[type="submit"]').click();

//     cy.get('.error-message').should('be.visible');
//   });

  
//   it('should successfully log in with valid credentials', () => {
//     cy.get('input[name="username"]').type('validUsername');
//     cy.get('input[name="password"]').type('validPassword');
//     cy.get('button[type="submit"]').click();


//     cy.url().should('include', '/dashboard'); // Replace '/dashboard' with the URL of the dashboard page
//     cy.get('.welcome-message').should('be.visible');
//   });
 });


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
