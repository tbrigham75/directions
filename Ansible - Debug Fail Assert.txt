Testing
1. How to debug in playbook
- name:  do a task
	 debug:
	 var:  system_uptime.stdout
	 
2.  Debug when something changes
- name: do a task
  debug:
	msg: "CMD ressulted in a change"
  when: system_uptime is changed
  
3.  Fail if or assert conditions warrant failure (Assert can be like test for a port or some condition before it proceeds"
vars: 
  should_fail_via_fault: true
  should_fail_via_assert: false
  should_fail_via_complex_assert: false

- name: Fail if
  fail:
	msg: "There was a failure:
  when: should_fail_via_fault
  
- name: Fail if assertion isn't validated
  assert:
	that: "should_fail_via_assert != true"

- name: Assertion can contain conditions
  assert:
	that:
	  - should_fail_via_fail != true
	  - should_fail_via_assert != true
	  - should_fail_via_complex_assertassert != true