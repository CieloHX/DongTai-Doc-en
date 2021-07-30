The built-in hook points can meet most situations, but in order to explore the vulnerabilities outside the built-in strategy, custom hook points(source point, propagation point, sink point) must be involved; The following describes the relevant content of the hook point configuration of the DongTai IAST.

### Custom Hook Rules

> hook point grammar

Custom rule: https://iast.huoxian.cn/setting/hookRule

Rule classification: 
- Stain source method rules(source method): detect the data from http request, rules are built in the agent and no need to do any configuration.

- Propagation method rules: used to deal with the situation that some taints are not related. If the internal logic of the method is too complicated to automatically recognize the taint changes, that could be fixed by configuring the propagation path

- Filter method rule: being used to exclude false positives and dig 0 day, generally do not need to configure that rule

- Dangerous method rules(sink method): need custom rules to trigger vulnerability method

#### Create rules for interfaces

**Scenario:**

We found that there are a large number of deserialization vulnerabilities caused by reading object methods in the open source of Java framework. Through the in-depth analysis, finding that most of class inherit from the InputStream interface and implement the reading method. So I don’t want to add a rule for each class, since the objects of these rules are repeated and the added object will increase the maintenance cost. So, how to solve the vulnerability IAST?

The rule of the DongTai IAST supports the setting of inheritance of relationships, which could be set to: only detect the current class and current subclasses, meanwhile, the agent will do a deep analysis of the inheritance relationship of each class, and sort out all parent classes and interface for the current class(The parent class of parent class and its interfaces can also be sorted out, and in the same way, it will be finished at the level of the subclasses of Object); then, when the hook rule is matched, the current class or its inherited classes and interfaces will be searched according to the configured inheritance relationship to judge whether the hook rule is hit. Therefore, in the above scenario, directly set the inheritance relationship to merely subclasses pointing to the methods of interface `java.io.ObjectInput.readObject()`.

![interface demo](https://hxsecurity.github.io/DongTai-Doc/doc/assets/bugbountry/interface_demo.png)



### N Day vulnerability cannot be detected and troubleshooting
If you find that the vulnerabilities of historical N Day cannot be detected, you can contact [technical support](https://hxsecurity.github.io/DongTai-Doc/doc/aboutus/support) for help or debug the history of vulnerabilities in order to research.

