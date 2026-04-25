# Parabank Basic Operations Test Plan

## Application Overview

ParaBank is a demo online banking application designed for testing purposes. This test plan covers basic operational workflows including user registration, login/authentication, account lookup, and navigation. The application provides features for customer account management, fund transfers, bill payment, and account history viewing. All tests assume the application is in a fresh/clean state.

## Test Scenarios

### 1. Application Navigation and Layout

**Seed:** `tests/seed.spec.ts`

#### 1.1. Verify home page loads successfully with all main elements

**File:** `tests/navigation/homepage-load.spec.ts`

**Steps:**
  1. Navigate to https://parabank.parasoft.com/parabank/index.htm
    - expect: Page title is 'ParaBank | Welcome | Online Banking'
    - expect: Customer Login section is visible with Username and Password fields
    - expect: Register link is present
    - expect: Forgot login info? link is present
  2. Verify the main navigation menu in the header
    - expect: About Us link is visible
    - expect: Services link is visible
    - expect: Products link is visible
    - expect: Admin Page link is visible
  3. Verify the ATM Services section is visible
    - expect: Withdraw Funds link is present
    - expect: Transfer Funds link is present
    - expect: Check Balances link is present
    - expect: Make Deposits link is present
  4. Verify the Online Services section is visible
    - expect: Bill Pay link is present
    - expect: Account History link is present
    - expect: Transfer Funds link is present
  5. Verify the footer navigation is present
    - expect: Home link is present in footer
    - expect: About Us link is present in footer
    - expect: Contact Us link is present in footer
    - expect: Copyright text is displayed

#### 1.2. Verify About Us page loads and displays company information

**File:** `tests/navigation/about-page.spec.ts`

**Steps:**
  1. Click on About Us link
    - expect: Page title is 'ParaBank | About Us'
    - expect: URL contains 'about.htm'
    - expect: Company information is displayed
  2. Verify About Us page content
    - expect: Heading 'ParaSoft Demo Website' is visible
    - expect: Text indicating ParaBank is a demo site is displayed
    - expect: Information about Parasoft contact details is present
  3. Click on www.parasoft.com link in content
    - expect: External link opens successfully
    - expect: User is redirected to www.parasoft.com

#### 1.3. Verify Services page displays available banking services

**File:** `tests/navigation/services-page.spec.ts`

**Steps:**
  1. Click on Services link
    - expect: Page title is 'ParaBank | Services'
    - expect: URL contains 'services.htm'
    - expect: Services content is loaded
  2. Verify page displays service information
    - expect: Page contains information about available services
    - expect: SOAP web services are documented
    - expect: Service endpoints are listed

#### 1.4. Verify Contact Us page loads with contact information

**File:** `tests/navigation/contact-page.spec.ts`

**Steps:**
  1. Click on Contact Us link in footer
    - expect: Page title is 'ParaBank | Contact Us'
    - expect: URL contains 'contact.htm'

#### 1.5. Verify Admin Page loads with administrative controls

**File:** `tests/navigation/admin-page.spec.ts`

**Steps:**
  1. Click on Admin Page link
    - expect: Page title is 'ParaBank | Administration'
    - expect: URL contains 'admin.htm'
    - expect: Administrative interface is displayed
  2. Verify admin control panels are present
    - expect: Database Initialize button is visible
    - expect: Database Clean button is visible
    - expect: JMS Service Status is displayed
    - expect: Service Shutdown button is available
  3. Verify Data Access Mode radio buttons are present
    - expect: SOAP option is available
    - expect: REST (XML) option is available
    - expect: REST (JSON) option is available
    - expect: JDBC option is available
    - expect: SOAP is selected by default

### 2. User Registration Flow

**Seed:** `tests/seed.spec.ts`

#### 2.1. Navigate to registration page and verify form fields

**File:** `tests/registration/registration-form-load.spec.ts`

**Steps:**
  1. Navigate to home page and click Register link
    - expect: Page title is 'ParaBank | Register for Free Online Account Access'
    - expect: URL contains 'register.htm'
    - expect: Heading 'Signing up is easy!' is displayed
  2. Verify all registration form fields are present
    - expect: First Name field is present
    - expect: Last Name field is present
    - expect: Address field is present
    - expect: City field is present
    - expect: State field is present
    - expect: Zip Code field is present
  3. Verify contact and account fields are present
    - expect: Phone Number field is present
    - expect: SSN field is present
    - expect: Username field is present
    - expect: Password field is present
    - expect: Confirm password field is present
  4. Verify Register button is present
    - expect: Register button is clickable
    - expect: Button text reads 'Register'

#### 2.2. Test successful user registration with valid data

**File:** `tests/registration/successful-registration.spec.ts`

**Steps:**
  1. Navigate to registration page
    - expect: Registration form is loaded and ready
  2. Enter valid first name: John
    - expect: Text is entered in First Name field
  3. Enter valid last name: Smith
    - expect: Text is entered in Last Name field
  4. Enter valid address: 123 Main Street
    - expect: Address is entered successfully
  5. Enter city: Springfield
    - expect: City is entered successfully
  6. Enter state: IL
    - expect: State is entered successfully
  7. Enter zip code: 62701
    - expect: Zip code is entered successfully
  8. Enter phone number: 555-1234
    - expect: Phone number is entered successfully
  9. Enter valid SSN: 123-45-6789
    - expect: SSN is entered successfully
  10. Enter unique username: johnsmith_test
    - expect: Username is entered successfully
  11. Enter password: P@ssw0rd123
    - expect: Password is entered successfully
    - expect: Password characters are masked
  12. Enter matching confirmation password: P@ssw0rd123
    - expect: Confirmation password is entered successfully
    - expect: Password characters are masked
  13. Click Register button
    - expect: Registration is successful
    - expect: Success message is displayed or user is redirected to dashboard
    - expect: New account can be used for login

#### 2.3. Test registration with empty required fields

**File:** `tests/registration/empty-fields-validation.spec.ts`

**Steps:**
  1. Navigate to registration page
    - expect: Registration form is loaded
  2. Leave First Name field empty and click Register
    - expect: Validation error is displayed for First Name
    - expect: Form is not submitted

#### 2.4. Test registration with mismatched passwords

**File:** `tests/registration/password-mismatch-validation.spec.ts`

**Steps:**
  1. Navigate to registration page and fill all required fields
    - expect: Form is populated with valid data except password
  2. Enter password: P@ssw0rd123 and confirmation: P@ssw0rd124
    - expect: Passwords are entered with mismatch
  3. Click Register button
    - expect: Validation error is displayed indicating password mismatch
    - expect: Form is not submitted
    - expect: Error message guides user to match passwords

#### 2.5. Test registration with invalid SSN format

**File:** `tests/registration/ssn-format-validation.spec.ts`

**Steps:**
  1. Navigate to registration page and fill all fields except SSN
    - expect: Form is ready for SSN input
  2. Enter invalid SSN: INVALID
    - expect: Invalid SSN format is entered
  3. Click Register button
    - expect: Validation error is displayed for SSN format
    - expect: Form is not submitted

### 3. User Authentication Flow

**Seed:** `tests/seed.spec.ts`

#### 3.1. Verify login form elements are present on home page

**File:** `tests/authentication/login-form-elements.spec.ts`

**Steps:**
  1. Navigate to home page
    - expect: Login form is visible
    - expect: Heading 'Customer Login' is displayed
  2. Verify login form contains required fields
    - expect: Username field is present and focused
    - expect: Password field is present
    - expect: Log In button is present and clickable
  3. Verify helper links are present
    - expect: Forgot login info? link is present
    - expect: Register link is present

#### 3.2. Test login with empty credentials

**File:** `tests/authentication/login-empty-credentials.spec.ts`

**Steps:**
  1. Leave Username and Password fields empty
    - expect: Fields remain empty
  2. Click Log In button
    - expect: Error message is displayed
    - expect: Login is rejected
    - expect: User remains on home page

#### 3.3. Test login with empty username only

**File:** `tests/authentication/login-empty-username.spec.ts`

**Steps:**
  1. Leave Username field empty and enter password in Password field
    - expect: Password is entered
    - expect: Username field is empty
  2. Click Log In button
    - expect: Validation error is displayed
    - expect: Login is rejected

#### 3.4. Test login with empty password only

**File:** `tests/authentication/login-empty-password.spec.ts`

**Steps:**
  1. Enter username but leave Password field empty
    - expect: Username is entered
    - expect: Password field is empty
  2. Click Log In button
    - expect: Validation error is displayed
    - expect: Login is rejected

#### 3.5. Test login with invalid credentials

**File:** `tests/authentication/login-invalid-credentials.spec.ts`

**Steps:**
  1. Enter invalid username: nonexistent_user
    - expect: Username is entered
  2. Enter invalid password: wrongpassword
    - expect: Password is entered
  3. Click Log In button
    - expect: Login fails with error message
    - expect: Error message indicates invalid login credentials
    - expect: User remains on home page or login page

#### 3.6. Test successful login with valid credentials

**File:** `tests/authentication/login-successful.spec.ts`

**Steps:**
  1. First register a new user account via registration flow
    - expect: User account is created successfully
    - expect: Credentials are available for login
  2. Navigate to home page
    - expect: Login form is displayed
  3. Enter valid username in Username field
    - expect: Username is entered
  4. Enter valid password in Password field
    - expect: Password is entered and masked
  5. Click Log In button
    - expect: Login is successful
    - expect: User is redirected to customer dashboard or account page
    - expect: User session is established

### 4. Account Recovery Flow

**Seed:** `tests/seed.spec.ts`

#### 4.1. Verify customer lookup form loads with required fields

**File:** `tests/account-recovery/lookup-form-load.spec.ts`

**Steps:**
  1. Click on Forgot login info? link
    - expect: Page title is 'ParaBank | Customer Lookup'
    - expect: URL contains 'lookup.htm'
    - expect: Heading 'Customer Lookup' is displayed
  2. Verify lookup form contains all required fields
    - expect: First Name field is present
    - expect: Last Name field is present
    - expect: Address field is present
    - expect: City field is present
    - expect: State field is present
    - expect: Zip Code field is present
    - expect: SSN field is present
  3. Verify Find My Login Info button is present
    - expect: Button is clickable
    - expect: Button text reads 'Find My Login Info'

#### 4.2. Test account lookup with empty fields

**File:** `tests/account-recovery/lookup-empty-fields.spec.ts`

**Steps:**
  1. Navigate to Customer Lookup page
    - expect: Lookup form is loaded
  2. Leave all fields empty and click Find My Login Info button
    - expect: Validation error is displayed
    - expect: Error indicates required fields are missing
    - expect: Lookup is not processed

#### 4.3. Test account lookup with partial information

**File:** `tests/account-recovery/lookup-partial-info.spec.ts`

**Steps:**
  1. Navigate to Customer Lookup page
    - expect: Lookup form is loaded
  2. Enter only First Name and Last Name, leave other fields empty
    - expect: First Name and Last Name are entered
  3. Click Find My Login Info button
    - expect: Error message is displayed
    - expect: Message indicates that all required fields must be completed

#### 4.4. Test account lookup with non-matching information

**File:** `tests/account-recovery/lookup-non-matching.spec.ts`

**Steps:**
  1. Navigate to Customer Lookup page
    - expect: Lookup form is loaded
  2. Enter all fields with information that doesn't match any registered customer
    - expect: All fields are populated with invalid/non-matching data
  3. Click Find My Login Info button
    - expect: Lookup fails
    - expect: Error message indicates that no matching customer found
    - expect: Login information is not retrieved

### 5. Data Validation and Input Handling

**Seed:** `tests/seed.spec.ts`

#### 5.1. Test special characters in text fields during registration

**File:** `tests/validation/special-characters-input.spec.ts`

**Steps:**
  1. Navigate to registration page
    - expect: Registration form is loaded
  2. Enter special characters in First Name: @#$%
    - expect: Special characters are entered or rejected based on validation rules
  3. Submit form
    - expect: System either accepts/validates the input appropriately or displays validation error

#### 5.2. Test numeric-only fields accept only numbers

**File:** `tests/validation/numeric-field-validation.spec.ts`

**Steps:**
  1. Navigate to registration page
    - expect: Registration form is loaded
  2. Attempt to enter letters in Zip Code field: abcde
    - expect: Field either rejects non-numeric input or system validates on submission
  3. Submit form
    - expect: Validation error is displayed for invalid zip code format
    - expect: Valid format appears to be numeric only

#### 5.3. Test maximum character limits in form fields

**File:** `tests/validation/field-length-limits.spec.ts`

**Steps:**
  1. Navigate to registration page
    - expect: Registration form is loaded
  2. Attempt to enter very long text in Username field (200+ characters)
    - expect: Field limits input to maximum allowed characters or accepts and validates on submission
  3. Observe field behavior
    - expect: Field has appropriate length constraints

#### 5.4. Test SQL injection prevention in text fields

**File:** `tests/validation/sql-injection-prevention.spec.ts`

**Steps:**
  1. Navigate to registration page
    - expect: Registration form is loaded
  2. Enter SQL injection attempt in First Name: ' OR '1'='1
    - expect: Input is submitted
  3. Complete registration with this malicious input
    - expect: System safely handles the input
    - expect: No SQL errors are displayed
    - expect: Data is stored safely

### 6. Link and Navigation Verification

**Seed:** `tests/seed.spec.ts`

#### 6.1. Verify all header navigation links are functional

**File:** `tests/links/header-navigation-links.spec.ts`

**Steps:**
  1. From home page, click About Us link in header
    - expect: Page navigates to About Us page
    - expect: URL contains 'about.htm'
    - expect: Page title is 'ParaBank | About Us'
  2. Navigate back to home and click Services link
    - expect: Page navigates to Services page
    - expect: URL contains 'services.htm'
  3. Click on Admin Page link
    - expect: Page navigates to Admin page
    - expect: URL contains 'admin.htm'

#### 6.2. Verify ParaBank logo links to home page

**File:** `tests/links/logo-home-link.spec.ts`

**Steps:**
  1. Navigate to any page other than home (e.g., About Us)
    - expect: User is on non-home page
  2. Click on ParaBank logo
    - expect: Page navigates to home page
    - expect: URL is home page URL
    - expect: Home page content is displayed

#### 6.3. Verify footer navigation links are functional

**File:** `tests/links/footer-navigation-links.spec.ts`

**Steps:**
  1. Scroll to footer of home page
    - expect: Footer is visible with navigation links
  2. Click Home link in footer
    - expect: Page remains on or navigates to home page
  3. Click About Us link in footer
    - expect: Page navigates to About Us page
  4. Click Services link in footer
    - expect: Page navigates to Services page

#### 6.4. Verify external links open in appropriate manner

**File:** `tests/links/external-links.spec.ts`

**Steps:**
  1. From About Us page, click www.parasoft.com link
    - expect: External link navigates to www.parasoft.com
    - expect: Page opens (may open in new tab/window)
  2. From home page, click Products link
    - expect: External Products link works
    - expect: User is directed to products page
