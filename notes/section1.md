#  Section 1 

```systemverilog
class transaction;
    randc bit [7:0] data;
    task display();
        $display("Value of Data : %0d",this.data);
    endtask
    
endclass

module testbench;
    transaction t;
    reg [7:0] data;
    initial begin
        t = new();
        for(int i=0;i<10;i++) begin
            t.randomize();
            data = t.data;
            t.display();
        end
    end
    
initial begin
    $dumpfile("dump.vcd");
    $dumpvars;
    #200;
    $finish();
end
    
endmodule
```

### EDA Playground

- Design code (DUT code) and Testbench code
- Languages used are SystemVerilog 
- Tools used are Aldec Riviera Pro 2022.4
  - rest of the simulators the access is provided using company account

- Compile options
- Run time
  - In code there must `$dumpfile` and `$dumpvars` along will Open EPWave checked will display waveforms
  - 