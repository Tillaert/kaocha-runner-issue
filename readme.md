# Incorrect error reporting reproduction project

This project is to show incorrect error reporting when using the polylith-koacha test runner. https://github.com/imrekoszo/polylith-kaocha/issues/8

It has a deliberate syntax error in `bases/ba/src/repo_case.ba.core.clj`. 

To run with default test runner:

```bash
clojure -Srepro -M:poly test project:pr-default
```

To run with kaocha:

```bash
clojure -Srepro -M:poly test project:pr-kaocha
```

## Output

### Default runner

The default runner shows the compilation error: `Unable to resolve symbol: b in this context`

```bash
Projects to run tests from: pr-default

Running tests for the pr-default project using test runner: Polylith built-in clojure.test runner...
Running tests from the pr-default project, including 1 brick: ba
clojure.lang.ExceptionInfo: Error while evaluating form (do (clojure.core/use (quote clojure.test)) (clojure.core/require (quote repo-case.ba.core-test)) (clojure.test/run-tests (quote repo-case.ba.core-test))) in class-loader. Cause: java.lang.reflect.InvocationTargetException; Syntax error compiling at (repo_case/ba/core.clj:4:1).; java.lang.RuntimeException: Unable to resolve symbol: b in this context {:form (do (clojure.core/use (quote clojure.test)) (clojure.core/require (quote repo-case.ba.core-test)) (clojure.test/run-tests (quote repo-case.ba.core-test)))}
        at polylith.clj.core.test_runner_orchestrator.core$__GT_eval_in_project$fn__9069.invoke(core.clj:81)
        at polylith.clj.core.clojure_test_test_runner.core$run_test_statements$fn__32146.invoke(core.clj:59)
        at polylith.clj.core.clojure_test_test_runner.core$run_test_statements.invokeStatic(core.clj:58)
        at polylith.clj.core.clojure_test_test_runner.core$run_test_statements.invoke(core.clj:52)
        at polylith.clj.core.clojure_test_test_runner.core$create$reify__32173.run_tests(core.clj:98)
        at polylith.clj.core.test_runner_orchestrator.core$run_tests_for_project_with_test_runner.invokeStatic(core.clj:70)
        at polylith.clj.core.test_runner_orchestrator.core$run_tests_for_project_with_test_runner.invoke(core.clj:59)
        at polylith.clj.core.test_runner_orchestrator.core$run_tests_for_project.invokeStatic(core.clj:128)
        at polylith.clj.core.test_runner_orchestrator.core$run_tests_for_project.invoke(core.clj:100)
        at clojure.core$map$fn__5931$fn__5932.invoke(core.clj:2759)
        at clojure.core$map$fn__5931$fn__5932.invoke(core.clj:2759)
        at clojure.lang.ArraySeq.reduce(ArraySeq.java:114)
        at clojure.core$transduce.invokeStatic(core.clj:6946)
        at clojure.core$transduce.invoke(core.clj:6933)
        at polylith.clj.core.test_runner_orchestrator.core$run.invokeStatic(core.clj:183)
        at polylith.clj.core.test_runner_orchestrator.core$run.invoke(core.clj:168)
        at polylith.clj.core.test_runner_orchestrator.interface$run.invokeStatic(interface.clj:5)
        at polylith.clj.core.test_runner_orchestrator.interface$run.invoke(interface.clj:4)
        at polylith.clj.core.command.test$run.invokeStatic(test.clj:11)
        at polylith.clj.core.command.test$run.invoke(test.clj:5)
        at polylith.clj.core.command.core$execute.invokeStatic(core.clj:88)
        at polylith.clj.core.command.core$execute.invoke(core.clj:63)
        at polylith.clj.core.command.interface$execute_command.invokeStatic(interface.clj:5)
        at polylith.clj.core.command.interface$execute_command.invoke(interface.clj:4)
        at polylith.clj.core.poly_cli.core$_main.invokeStatic(core.clj:33)
        at polylith.clj.core.poly_cli.core$_main.doInvoke(core.clj:7)
        at clojure.lang.RestFn.applyTo(RestFn.java:137)
        at clojure.lang.Var.applyTo(Var.java:705)
        at clojure.core$apply.invokeStatic(core.clj:667)
        at clojure.main$main_opt.invokeStatic(main.clj:514)
        at clojure.main$main_opt.invoke(main.clj:510)
        at clojure.main$main.invokeStatic(main.clj:664)
        at clojure.main$main.doInvoke(main.clj:616)
        at clojure.lang.RestFn.applyTo(RestFn.java:137)
        at clojure.lang.Var.applyTo(Var.java:705)
        at clojure.main.main(main.java:40)
Caused by: java.lang.reflect.InvocationTargetException
        at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
        at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.base/java.lang.reflect.Method.invoke(Method.java:566)
        at polylith.clj.core.common.class_loader$invoke_in_STAR_.invokeStatic(class_loader.clj:31)
        at polylith.clj.core.common.class_loader$invoke_in_STAR_.doInvoke(class_loader.clj:27)
        at clojure.lang.RestFn.invoke(RestFn.java:494)
        at polylith.clj.core.common.class_loader$eval_in_STAR_$print_read_eval__287.invoke(class_loader.clj:49)
        at polylith.clj.core.common.class_loader$eval_in_STAR_.invokeStatic(class_loader.clj:51)
        at polylith.clj.core.common.class_loader$eval_in_STAR_.invoke(class_loader.clj:45)
        at polylith.clj.core.common.class_loader$eval_in.invokeStatic(class_loader.clj:61)
        at polylith.clj.core.common.class_loader$eval_in.invoke(class_loader.clj:60)
        at polylith.clj.core.common.interface$eval_in.invokeStatic(interface.clj:23)
        at polylith.clj.core.common.interface$eval_in.invoke(interface.clj:22)
        at polylith.clj.core.test_runner_orchestrator.core$__GT_eval_in_project$fn__9069.invoke(core.clj:79)
        ... 35 more
Caused by: Syntax error compiling at (repo_case/ba/core.clj:4:1).
        at clojure.lang.Compiler.analyze(Compiler.java:6808)
        at clojure.lang.Compiler.access$300(Compiler.java:38)
        at clojure.lang.Compiler$DefExpr$Parser.parse(Compiler.java:596)
        at clojure.lang.Compiler.analyzeSeq(Compiler.java:7107)
        at clojure.lang.Compiler.analyze(Compiler.java:6789)
        at clojure.lang.Compiler.analyze(Compiler.java:6745)
        at clojure.lang.Compiler.eval(Compiler.java:7181)
        at clojure.lang.Compiler.load(Compiler.java:7636)
        at clojure.lang.RT.loadResourceScript(RT.java:381)
        at clojure.lang.RT.loadResourceScript(RT.java:372)
        at clojure.lang.RT.load(RT.java:459)
        at clojure.lang.RT.load(RT.java:424)
        at clojure.core$load$fn__6839.invoke(core.clj:6126)
        at clojure.core$load.invokeStatic(core.clj:6125)
        at clojure.core$load.doInvoke(core.clj:6109)
        at clojure.lang.RestFn.invoke(RestFn.java:408)
        at clojure.core$load_one.invokeStatic(core.clj:5908)
        at clojure.core$load_one.invoke(core.clj:5903)
        at clojure.core$load_lib$fn__6780.invoke(core.clj:5948)
        at clojure.core$load_lib.invokeStatic(core.clj:5947)
        at clojure.core$load_lib.doInvoke(core.clj:5928)
        at clojure.lang.RestFn.applyTo(RestFn.java:142)
        at clojure.core$apply.invokeStatic(core.clj:667)
        at clojure.core$load_libs.invokeStatic(core.clj:5985)
        at clojure.core$load_libs.doInvoke(core.clj:5969)
        at clojure.lang.RestFn.applyTo(RestFn.java:137)
        at clojure.core$apply.invokeStatic(core.clj:667)
        at clojure.core$require.invokeStatic(core.clj:6007)
        at clojure.core$require.doInvoke(core.clj:6007)
        at clojure.lang.RestFn.invoke(RestFn.java:421)
        at repo_case.ba.core_test$eval146$loading__6721__auto____147.invoke(core_test.clj:1)
        at repo_case.ba.core_test$eval146.invokeStatic(core_test.clj:1)
        at repo_case.ba.core_test$eval146.invoke(core_test.clj:1)
        at clojure.lang.Compiler.eval(Compiler.java:7177)
        at clojure.lang.Compiler.eval(Compiler.java:7166)
        at clojure.lang.Compiler.load(Compiler.java:7636)
        at clojure.lang.RT.loadResourceScript(RT.java:381)
        at clojure.lang.RT.loadResourceScript(RT.java:372)
        at clojure.lang.RT.load(RT.java:459)
        at clojure.lang.RT.load(RT.java:424)
        at clojure.core$load$fn__6839.invoke(core.clj:6126)
        at clojure.core$load.invokeStatic(core.clj:6125)
        at clojure.core$load.doInvoke(core.clj:6109)
        at clojure.lang.RestFn.invoke(RestFn.java:408)
        at clojure.core$load_one.invokeStatic(core.clj:5908)
        at clojure.core$load_one.invoke(core.clj:5903)
        at clojure.core$load_lib$fn__6780.invoke(core.clj:5948)
        at clojure.core$load_lib.invokeStatic(core.clj:5947)
        at clojure.core$load_lib.doInvoke(core.clj:5928)
        at clojure.lang.RestFn.applyTo(RestFn.java:142)
        at clojure.core$apply.invokeStatic(core.clj:667)
        at clojure.core$load_libs.invokeStatic(core.clj:5985)
        at clojure.core$load_libs.doInvoke(core.clj:5969)
        at clojure.lang.RestFn.applyTo(RestFn.java:137)
        at clojure.core$apply.invokeStatic(core.clj:667)
        at clojure.core$require.invokeStatic(core.clj:6007)
        at clojure.core$require.doInvoke(core.clj:6007)
        at clojure.lang.RestFn.invoke(RestFn.java:408)
        at clojure.core$eval142.invokeStatic(NO_SOURCE_FILE:0)
        at clojure.core$eval142.invoke(NO_SOURCE_FILE)
        at clojure.lang.Compiler.eval(Compiler.java:7177)
        at clojure.lang.Compiler.eval(Compiler.java:7166)
        at clojure.lang.Compiler.eval(Compiler.java:7132)
        at clojure.core$eval.invokeStatic(core.clj:3214)
        at clojure.core$eval.invoke(core.clj:3210)
        at clojure.core$eval138.invokeStatic(NO_SOURCE_FILE:0)
        at clojure.core$eval138.invoke(NO_SOURCE_FILE)
        at clojure.lang.Compiler.eval(Compiler.java:7177)
        at clojure.lang.Compiler.eval(Compiler.java:7132)
        ... 50 more
Caused by: java.lang.RuntimeException: 
        at clojure.lang.Util.runtimeException(Util.java:221)
        at clojure.lang.Compiler.resolveIn(Compiler.java:7414)
        at clojure.lang.Compiler.resolve(Compiler.java:7358)
        at clojure.lang.Compiler.analyzeSymbol(Compiler.java:7319)
        at clojure.lang.Compiler.analyze(Compiler.java:6768)
        ... 118 more
Couldn't run test statement for the pr-default project: (do (clojure.core/use (quote clojure.test)) (clojure.core/require (quote repo-case.ba.core-test)) (clojure.test/run-tests (quote repo-case.ba.core-test))) clojure.lang.ExceptionInfo: Error while evaluating form (do (clojure.core/use (quote clojure.test)) (clojure.core/require (quote repo-case.ba.core-test)) (clojure.test/run-tests (quote repo-case.ba.core-test))) in class-loader. Cause: java.lang.reflect.InvocationTargetException; Syntax error compiling at (repo_case/ba/core.clj:4:1).; java.lang.RuntimeException: Unable to resolve symbol: b in this context {:form (do (clojure.core/use (quote clojure.test)) (clojure.core/require (quote repo-case.ba.core-test)) (clojure.test/run-tests (quote repo-case.ba.core-test)))}

Test results:  passes,  failures,  errors.
```

### polylith-kaocha


The kaocha runner shows this as a test result. It does not show the compilation error, rather an error that it can't find the namespace which contains the error.

```bash
Projects to run tests from: pr-kaocha

Running tests for the pr-kaocha project using test runner: polylith-kaocha...
[E]
Randomized with --seed 1813748497

ERROR in unit (repo_case/ba/core_test.clj:1)
Failed loading tests:
Exception: clojure.lang.Compiler$CompilerException: Syntax error compiling at (repo_case/ba/core_test.clj:1:1).
#:clojure.error{:phase :compile-syntax-check, :line 1, :column 1, :source "repo_case/ba/core_test.clj"}
 at clojure.core$throw_if.invokeStatic (core.clj:5867)
    ...
    repo_case.ba.core_test$eval4967$loading__6721__auto____4968.invoke (core_test.clj:1)
    repo_case.ba.core_test$eval4967.invokeStatic (core_test.clj:1)
    repo_case.ba.core_test$eval4967.invoke (core_test.clj:1)
    ...
    kaocha.ns$required_ns.invokeStatic (ns.clj:13)
    kaocha.ns$required_ns.invoke (ns.clj:11)
    kaocha.type.ns$eval3443$fn__3444.invoke (ns.clj:29)
    ...
    kaocha.testable$load.invokeStatic (testable.clj:94)
    kaocha.testable$load.invoke (testable.clj:75)
    kaocha.testable$load_testables.invokeStatic (testable.clj:152)
    kaocha.testable$load_testables.invoke (testable.clj:144)
    kaocha.load$load_test_namespaces.invokeStatic (load.clj:49)
    kaocha.load$load_test_namespaces.doInvoke (load.clj:37)
    ...
    kaocha.type.clojure.test$eval4865$fn__4866.invoke (test.clj:17)
    ...
    kaocha.testable$load.invokeStatic (testable.clj:94)
    kaocha.testable$load.invoke (testable.clj:75)
    kaocha.testable$load_testables.invokeStatic (testable.clj:152)
    kaocha.testable$load_testables.invoke (testable.clj:144)
    kaocha.api$test_plan.invokeStatic (api.clj:56)
    kaocha.api$test_plan.invoke (api.clj:49)
    kaocha.api$run$fn__2908.invoke (api.clj:101)
    ...
    kaocha.api$run.invokeStatic (api.clj:99)
    kaocha.api$run.invoke (api.clj:86)
    polylith_kaocha.kaocha_wrapper.runner$run_to_test_results_BANG_.invokeStatic (runner.clj:33)
    polylith_kaocha.kaocha_wrapper.runner$run_to_test_results_BANG_.invoke (runner.clj:31)
    polylith_kaocha.kaocha_wrapper.runner$run_with_complete_config.invokeStatic (runner.clj:47)
    polylith_kaocha.kaocha_wrapper.runner$run_with_complete_config.invoke (runner.clj:43)
    polylith_kaocha.kaocha_wrapper.runner$in_context_runner$run___4951.invoke (runner.clj:59)
    polylith_kaocha.kaocha_wrapper.config$execute_in_config_context$fn__3261.invoke (config.clj:82)
    ...
    polylith_kaocha.kaocha_wrapper.config$execute_in_config_context.invokeStatic (config.clj:81)
    polylith_kaocha.kaocha_wrapper.config$execute_in_config_context.invoke (config.clj:76)
    polylith_kaocha.kaocha_wrapper.runner$run_tests_with_kaocha.invokeStatic (runner.clj:63)
    polylith_kaocha.kaocha_wrapper.runner$run_tests_with_kaocha.invoke (runner.clj:61)
    polylith_kaocha.kaocha_wrapper.runner$run_tests.invokeStatic (runner.clj:72)
    polylith_kaocha.kaocha_wrapper.runner$run_tests.invoke (runner.clj:69)
    polylith_kaocha.kaocha_wrapper.interface.runner$run_tests.invokeStatic (runner.clj:6)
    polylith_kaocha.kaocha_wrapper.interface.runner$run_tests.invoke (runner.clj:5)
    ...
    jdk.internal.reflect.NativeMethodAccessorImpl.invoke0 (NativeMethodAccessorImpl.java:-2)
    jdk.internal.reflect.NativeMethodAccessorImpl.invoke (NativeMethodAccessorImpl.java:62)
    jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke (DelegatingMethodAccessorImpl.java:43)
    ...
    polylith.clj.core.common.class_loader$invoke_in_STAR_.invokeStatic (class_loader.clj:31)
    polylith.clj.core.common.class_loader$invoke_in_STAR_.doInvoke (class_loader.clj:27)
    ...
    polylith.clj.core.common.class_loader$eval_in_STAR_$print_read_eval__287.invoke (class_loader.clj:49)
    polylith.clj.core.common.class_loader$eval_in_STAR_.invokeStatic (class_loader.clj:51)
    polylith.clj.core.common.class_loader$eval_in_STAR_.invoke (class_loader.clj:45)
    polylith.clj.core.common.class_loader$eval_in.invokeStatic (class_loader.clj:61)
    polylith.clj.core.common.class_loader$eval_in.invoke (class_loader.clj:60)
    polylith.clj.core.common.interface$eval_in.invokeStatic (interface.clj:23)
    polylith.clj.core.common.interface$eval_in.invoke (interface.clj:22)
    polylith.clj.core.test_runner_orchestrator.core$__GT_eval_in_project$fn__9069.invoke (core.clj:79)
    polylith_kaocha.kaocha_test_runner.core$apply_in_project.invokeStatic (core.clj:83)
    polylith_kaocha.kaocha_test_runner.core$apply_in_project.invoke (core.clj:80)
    polylith_kaocha.kaocha_test_runner.core$create$reify__32097.run_tests (core.clj:124)
    polylith.clj.core.test_runner_orchestrator.core$run_tests_for_project_with_test_runner.invokeStatic (core.clj:70)
    polylith.clj.core.test_runner_orchestrator.core$run_tests_for_project_with_test_runner.invoke (core.clj:59)
    polylith.clj.core.test_runner_orchestrator.core$run_tests_for_project.invokeStatic (core.clj:128)
    polylith.clj.core.test_runner_orchestrator.core$run_tests_for_project.invoke (core.clj:100)
    ...
    polylith.clj.core.test_runner_orchestrator.core$run.invokeStatic (core.clj:183)
    polylith.clj.core.test_runner_orchestrator.core$run.invoke (core.clj:168)
    polylith.clj.core.test_runner_orchestrator.interface$run.invokeStatic (interface.clj:5)
    polylith.clj.core.test_runner_orchestrator.interface$run.invoke (interface.clj:4)
    polylith.clj.core.command.test$run.invokeStatic (test.clj:11)
    polylith.clj.core.command.test$run.invoke (test.clj:5)
    polylith.clj.core.command.core$execute.invokeStatic (core.clj:88)
    polylith.clj.core.command.core$execute.invoke (core.clj:63)
    polylith.clj.core.command.interface$execute_command.invokeStatic (interface.clj:5)
    polylith.clj.core.command.interface$execute_command.invoke (interface.clj:4)
    polylith.clj.core.poly_cli.core$_main.invokeStatic (core.clj:33)
    polylith.clj.core.poly_cli.core$_main.doInvoke (core.clj:7)
    ...
Caused by: java.lang.Exception: namespace 'repo-case.ba.core' not found
 at clojure.core$apply.invokeStatic (core.clj:667)
    ...
    repo_case.ba.core_test$eval4967$loading__6721__auto____4968.invoke (core_test.clj:1)
    repo_case.ba.core_test$eval4967.invokeStatic (core_test.clj:1)
    repo_case.ba.core_test$eval4967.invoke (core_test.clj:1)
    ...
    kaocha.ns$required_ns.invokeStatic (ns.clj:13)
    kaocha.ns$required_ns.invoke (ns.clj:11)
    kaocha.type.ns$eval3443$fn__3444.invoke (ns.clj:29)
    ...
    kaocha.testable$load.invokeStatic (testable.clj:94)
    kaocha.testable$load.invoke (testable.clj:75)
    kaocha.testable$load_testables.invokeStatic (testable.clj:152)
    kaocha.testable$load_testables.invoke (testable.clj:144)
    kaocha.load$load_test_namespaces.invokeStatic (load.clj:49)
    kaocha.load$load_test_namespaces.doInvoke (load.clj:37)
    ...
    kaocha.type.clojure.test$eval4865$fn__4866.invoke (test.clj:17)
    ...
    kaocha.testable$load.invokeStatic (testable.clj:94)
    kaocha.testable$load.invoke (testable.clj:75)
    kaocha.testable$load_testables.invokeStatic (testable.clj:152)
    kaocha.testable$load_testables.invoke (testable.clj:144)
    kaocha.api$test_plan.invokeStatic (api.clj:56)
    kaocha.api$test_plan.invoke (api.clj:49)
    kaocha.api$run$fn__2908.invoke (api.clj:101)
    ...
    kaocha.api$run.invokeStatic (api.clj:99)
    kaocha.api$run.invoke (api.clj:86)
    polylith_kaocha.kaocha_wrapper.runner$run_to_test_results_BANG_.invokeStatic (runner.clj:33)
    polylith_kaocha.kaocha_wrapper.runner$run_to_test_results_BANG_.invoke (runner.clj:31)
    polylith_kaocha.kaocha_wrapper.runner$run_with_complete_config.invokeStatic (runner.clj:47)
    polylith_kaocha.kaocha_wrapper.runner$run_with_complete_config.invoke (runner.clj:43)
    polylith_kaocha.kaocha_wrapper.runner$in_context_runner$run___4951.invoke (runner.clj:59)
    polylith_kaocha.kaocha_wrapper.config$execute_in_config_context$fn__3261.invoke (config.clj:82)
    ...
    polylith_kaocha.kaocha_wrapper.config$execute_in_config_context.invokeStatic (config.clj:81)
    polylith_kaocha.kaocha_wrapper.config$execute_in_config_context.invoke (config.clj:76)
    polylith_kaocha.kaocha_wrapper.runner$run_tests_with_kaocha.invokeStatic (runner.clj:63)
    polylith_kaocha.kaocha_wrapper.runner$run_tests_with_kaocha.invoke (runner.clj:61)
    polylith_kaocha.kaocha_wrapper.runner$run_tests.invokeStatic (runner.clj:72)
    polylith_kaocha.kaocha_wrapper.runner$run_tests.invoke (runner.clj:69)
    polylith_kaocha.kaocha_wrapper.interface.runner$run_tests.invokeStatic (runner.clj:6)
    polylith_kaocha.kaocha_wrapper.interface.runner$run_tests.invoke (runner.clj:5)
    ...
    jdk.internal.reflect.NativeMethodAccessorImpl.invoke0 (NativeMethodAccessorImpl.java:-2)
    jdk.internal.reflect.NativeMethodAccessorImpl.invoke (NativeMethodAccessorImpl.java:62)
    jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke (DelegatingMethodAccessorImpl.java:43)
    ...
    polylith.clj.core.common.class_loader$invoke_in_STAR_.invokeStatic (class_loader.clj:31)
    polylith.clj.core.common.class_loader$invoke_in_STAR_.doInvoke (class_loader.clj:27)
    ...
    polylith.clj.core.common.class_loader$eval_in_STAR_$print_read_eval__287.invoke (class_loader.clj:49)
    polylith.clj.core.common.class_loader$eval_in_STAR_.invokeStatic (class_loader.clj:51)
    polylith.clj.core.common.class_loader$eval_in_STAR_.invoke (class_loader.clj:45)
    polylith.clj.core.common.class_loader$eval_in.invokeStatic (class_loader.clj:61)
    polylith.clj.core.common.class_loader$eval_in.invoke (class_loader.clj:60)
    polylith.clj.core.common.interface$eval_in.invokeStatic (interface.clj:23)
    polylith.clj.core.common.interface$eval_in.invoke (interface.clj:22)
    polylith.clj.core.test_runner_orchestrator.core$__GT_eval_in_project$fn__9069.invoke (core.clj:79)
    polylith_kaocha.kaocha_test_runner.core$apply_in_project.invokeStatic (core.clj:83)
    polylith_kaocha.kaocha_test_runner.core$apply_in_project.invoke (core.clj:80)
    polylith_kaocha.kaocha_test_runner.core$create$reify__32097.run_tests (core.clj:124)
    polylith.clj.core.test_runner_orchestrator.core$run_tests_for_project_with_test_runner.invokeStatic (core.clj:70)
    polylith.clj.core.test_runner_orchestrator.core$run_tests_for_project_with_test_runner.invoke (core.clj:59)
    polylith.clj.core.test_runner_orchestrator.core$run_tests_for_project.invokeStatic (core.clj:128)
    polylith.clj.core.test_runner_orchestrator.core$run_tests_for_project.invoke (core.clj:100)
    ...
    polylith.clj.core.test_runner_orchestrator.core$run.invokeStatic (core.clj:183)
    polylith.clj.core.test_runner_orchestrator.core$run.invoke (core.clj:168)
    polylith.clj.core.test_runner_orchestrator.interface$run.invokeStatic (interface.clj:5)
    polylith.clj.core.test_runner_orchestrator.interface$run.invoke (interface.clj:4)
    polylith.clj.core.command.test$run.invokeStatic (test.clj:11)
    polylith.clj.core.command.test$run.invoke (test.clj:5)
    polylith.clj.core.command.core$execute.invokeStatic (core.clj:88)
    polylith.clj.core.command.core$execute.invoke (core.clj:63)
    polylith.clj.core.command.interface$execute_command.invokeStatic (interface.clj:5)
    polylith.clj.core.command.interface$execute_command.invoke (interface.clj:4)
    polylith.clj.core.poly_cli.core$_main.invokeStatic (core.clj:33)
    polylith.clj.core.poly_cli.core$_main.doInvoke (core.clj:7)
    ...
1 tests, 1 assertions, 1 errors, 0 failures.
Tests failed [polylith-kaocha]
```