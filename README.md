# LastPriceService
Download LastPriceService.zip and Import maven project into your IDE i.e. Eclipse IDE.

PriceRecord.java class has below 3 fields to get LastPrice via consumer.
  private final String id;
	private final Instant asOf;
	private final Map<String, Object> payload;

PriceRecordBuilder.java is builder class for PriceRecord to upload via producer.

Producer.java: Upload prices data 
Consumer.java: Read all the uploaded data and get the last price based on asOf field and process.
InMemoryLastPriceService.java:  Core implementation using Template Method for batch processing.. In-memory implementation - Thread-safe & Atomic

Run LastPriceApplication.java to start Producer and consumer in memory on same JVM.
Output:
        === PRODUCER + CONSUMER + BUILDER DEMO ===
        
        📤 REQUIREMENT 1-3: PRODUCER BATCH SEQUENCE
        ─────────────────────────────────────────
          1️⃣ startBatch()
        Batch id=c361a79e-5853-4070-8fb7-7dd9ed3df417
        👁️  REQUIREMENT: CONSUMER QUERIES
        ─────────────────────────────────
          Querying 3 instruments:
            AAPL: $349.90 @ 2026-01-12T09:23:31.878069Z
            GOOG: $349.70 @ 2026-01-12T09:23:29.878069Z
            INVALID: not found
        
        ⏰ REQUIREMENT: LAST BY asOf TIMESTAMP
        ─────────────────────────────────────
            AAPL: $349.90 @ 2026-01-12T09:23:31.878069Z
        
        🗑️  REQUIREMENT: CANCELLED = INVISIBLE
        ────────────────────────────────────
            CANCELLED_STOCK: not found
        
        🛡️  REQUIREMENT: RESILIENT TO ERRORS
        
        
        ───────────────────────────────────
        ✅ PASSED: Unknown batch rejected
        ✅ PASSED: Post-complete rejected
        
        🎉 ALL BUSINESS REQUIREMENTS DEMONSTRATED ✓
  OR
  Run Junit test case : LastPriceServiceTest.java
  
  


