# Accessibility

Building applications usable by as many people as possible. Oftentimes this means utilizing semantic HTML and ensuring the application works properly with various assistive technologies.

## Accessibility Tree

Similar to the DOM tree contains information for accessibility

A tree representation of the page focusing on information specific to accessibility. Each node in this tree contains information such as the *role*, *state*, *name* and *description*.

The accessibility tree is created from the DOM tree and kept in sync with it. Assistive technologies such as screen readers interact with the accessibility tree rather than directly with the DOM.

[Learn more](https://developer.mozilla.org/en-US/docs/Glossary/Accessibility_tree)

## Writing Accessible html

* Use Descriptive content, labels & alt attrivutes 
* Use Semantic elements 
* Test Keyboard controls meaning user can navigate in your website with only Keybaord 

## WAI-ARIA

The "Web Accessibility Initiative - Accessible Rich Internet Applications" specification for accessible HTML created by the World Wide Web Consortium (W3C). Oftentimes referred to as just ARIA, this contains a set of HTML attributes that can be added to provide extra information to the accessibility tree.

ARIA attributes are usually grouped into three main categories:

* **Roles**: _What the element is doing_, used to define the purpose of the element. These can be broken down into a few main subgroups:

	* **Landmark**: Major content areas, navigational landmarks. **Examples** [banner, main, navigation]
		
		```html 
		<!--The banner role is for defining a global site header, which usually includes a logo, company name, search icon, and possibly a slogan, generally at the top of the page.-->
			
		<div role="banner">
		  <img src="companylogo.svg" alt="my company name" />
		  <h1>Title</h1>
		  <p>Subtitle</p>
		</div>
			
		<!--The navigation role is used to identify major groups of links used for navigating through a website or page content.-->
			
		<div role="navigation" aria-label="Main">
		  <!-- list of links to main website locations -->
		</div>
		```
	🚀[Learn More about roles](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles)
		
	* **Structure**: Document structure information. **Examples** [tooltip, list, table]
			
		```html 
			
		<label for="password">Password:</label>
		<input aria-describedby="passwordrules" id="password" type="password" />
		<div hidden role="tooltip" id="passwordrules">
		  <p>
		      Password Rules:
		  </p>
		  <ul>
		    <li> Minimum of 8 characters</li>
		    <li> Include at least one lowercase letter, one uppercase letter, one number and one special character</li>
		    <li>Unique to this website</li>
		  </ul>
		</div>
		```
	🚀[Learn More about roles](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles)
		
	* **Widget**: Interactive elements. **Examples** [tab, searchbox, button]
			
		```html 
			<!--The button role identifies an element as a button to assistive technology such as screen readers. -->
			
			<div id="saveChanges" tabindex="0" role="button" aria-pressed="false">Save</div>
		```
	🚀[Learn More about roles](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles)
		
	* **Window**: Sub-windows in the browser. **Examples** [dialog, alert dialog]
		
		```html 
			<!-- The dialog role is used to mark up an HTML based application dialog or 
			window that separates content or UI from the rest of the web application or page -->
			
			<div role="dialog" aria-labelledby="dialog1Title" aria-describedby="dialog1Desc">
			  <h2 id="dialog1Title">Your personal details were successfully updated</h2>
			  <p id="dialog1Desc">You can change your details at any time in the user account section.</p>
			  <button>Close</button>
			</div>
		```
	🚀[Learn More about roles](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles)
	
	* **Live Region**: Regions with dynamically changing content.  **Examples** [timer, log, alert]
		
		```html 
			<ol role="log">
			 	<li>Chat Message 1</li>
			 	<li>Chat Message 2</li>
			 	<li>Chat Message 3</li>
			</ol>
		```
	🚀[Learn More about roles](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles)
	
	
	**Global States and Properties** The following global states and properties are supported by all roles and by all base markup elements.
	
	* **Aria live**: Indicates that an element will be updated, and describes the types of updates the user agents, assistive technologies, and user can expect from the live region.  **Examples** [off, polite, assertive]
	
		* **Off**: Don't Announce Changes 
		* **Polite**:  Notify users of updates but generally do not interrupt the current task, and updates take low priority.
		* **Assertive**: will immediately notify the user, and could potentially clear the speech queue of previous updates.
		
			```html 
				<div aria-live="polite"> 
				 	My Content will change
				</div>
			```
	🚀[Learn More about Aria Live](https://www.w3.org/TR/wai-aria-1.0/states_and_properties#aria-live)
	
	* **Aria Properties**: The following global states and properties are supported by all roles and by all base markup elements.  
	
		**Examples**
	
		* **aria-label**: label not visible on UI [Learn More](https://www.w3.org/TR/wai-aria-1.0/states_and_properties#aria-label)
		* **aria-labelledby**:  If the label text is visible on screen, authors SHOULD use `aria-labelledby` and SHOULD NOT use `aria-label`. [Learn More](https://www.w3.org/TR/wai-aria-1.0/states_and_properties#aria-labelledby) 
		* **aria-describedby**: The `aria-labelledby` attribute is similar to `aria-describedby` in that both reference other elements to calculate a text alternative, but a label should be concise, where a description is intended to provide more verbose information. [Learn More](https://www.w3.org/TR/wai-aria-1.0/states_and_properties#aria-describedby)
		
			```html 
				<div role="dialog" aria-labelledby="title">
				 	<h3 id="title">Successfully adding order</h3>
				</div>
			```
	🚀[Learn More about Aria Live](https://www.w3.org/TR/wai-aria-1.0/states_and_properties#aria-live)

	**Aria State** Provide statfull information about elements These attributes are used to support the [widget roles](https://www.w3.org/TR/wai-aria-1.0/roles#widget_roles).
	
	* **Aria live**: Indicates that an element will be updated, and describes the types of updates the user agents, assistive technologies, and user can expect from the live region.  **Examples** [off, polite, assertive]
	
		* **aria-checked**: Indicates the current "checked" state of checkboxes, radio buttons, and other [Learn More](https://www.w3.org/TR/wai-aria-1.0/states_and_properties#aria-checked)
		* **aria-disabled**: Element is disabled, so it is not editable or otherwise operable. [Learn More](https://www.w3.org/TR/wai-aria-1.0/states_and_properties#aria-disabled)
		* **aria-expanded**: Indicates whether the element, or another grouping element it controls, is currently expanded or collapsed. [Learn More](https://www.w3.org/TR/wai-aria-1.0/states_and_properties#aria-expanded)
		* **aria-hidden**: Indicates that the element and all of its descendants are not visible [Learn More](https://www.w3.org/TR/wai-aria-1.0/states_and_properties#aria-hidden)
		* **aria-pressed**: Toggle currently "pressed", The `aria-pressed` attribute is similar but not identical to the `aria-checked` attribute. Operating systems support pressed on `buttons` and checked on `checkboxes`. [Learn More](https://www.w3.org/TR/wai-aria-1.0/states_and_properties#aria-pressed)
		* **aria-selected**: Element is "selected"[Learn More](https://www.w3.org/TR/wai-aria-1.0/states_and_properties#aria-selected)
		
			
			```html 
				<div role="checkbox" aria-checked="true"> 
				 	I'm checked!
				</div>
			```


* **Properties**: _Extra meaning and characteristics of the element_, such as *labels*.

* **States**: _Current state of the element_, such as if it is *disabled*.

[Learn more](https://developer.mozilla.org/en-US/docs/Learn/Accessibility/WAI-ARIA_basics) 


## Other Concerns for Accessibility

* Broswer Compatibility
* CSS Accessibility [use contrast, legible fonts, mobile support, etc..]
* Internationalization (I18n)
	* Language Support 
	* Test with different `style` language
