## This repository documents java concepts

create or replace package employee_hike_pkg
is
procedure employee_hike(emp_id IN number);
function getManager(deptid IN DEPARTMENTS.DEPARTMENT_ID%type) RETURN VARCHAR2;
end;

create or replace package body employee_hike_pkg
is
  procedure employee_hike(emp_id IN number)
  is
    v_exp number(2);
    v_hike number(3,2);
    v_date date;
  Begin
   select sysdate into v_date from dual;
  end employee_hike; 
  
 function getManager(deptid IN DEPARTMENTS.DEPARTMENT_ID%type) RETURN VARCHAR2
  is
    v_name EMPLOYEES.FIRST_NAME%type; 
  begin
   select e.LAST_NAME into v_name from departments d 
    inner join employees e on e.EMPLOYEE_ID=d.MANAGER_ID and d.DEPARTMENT_ID=deptid;
  return v_name;
  EXCEPTION
   when NO_DATA_FOUND then 
     return 'no records found for input';
  end getManager;

end employee_hike_pkg;

//Procedure returning ref cursor
create or replace procedure getEmployeesByJob(p_job_id IN VARCHAR2, p_emp_refcursor IN OUT SYS_REFCURSOR)
IS
BEGIN
  OPEN p_emp_refcursor FOR select employee_id,last_name,job_id from employees where job_id=p_job_id;
END;


DECLARE
empid employees.employee_id%type;
lname employees.last_name%type;
jobId employees.job_id%type;
p_emp_refcursor SYS_REFCURSOR;

BEGIN
 getEmployeesByJob('SA_REP',p_emp_refcursor);
  LOOP
   FETCH p_emp_refcursor into empid, lname, jobId;
   EXIT WHEN p_emp_refcursor%NOTFOUND;
   dbms_output.put_line(empid||' '|| lname||' '|| jobId);
  END LOOP;
  close p_emp_refcursor;
END;

