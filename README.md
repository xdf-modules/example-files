# XDF example files

Example files to test XDF readers.

* [minimal.xdf](#minimalxdf)
* [clock\_resets.xdf](#clock_resetsxdf)
* [empty\_streams.xdf](#empty_streamsxdf)

## minimal.xdf

Minimal example file with two streams.

### Stream 0

3 `int16` channels, 9 samples

#### Header

``` xml
<info>
    <name>SendDataC</name>
    <type>EEG</type>
    <channel_count>3</channel_count>
    <nominal_srate>10</nominal_srate>
    <channel_format>int16</channel_format>
    <created_at>50942.723319709003</created_at>
    <desc/>
    <uid>xdfwriter_11_int</uid>
</info>
```

#### Footer

``` xml
<info>
    <writer>LabRecorder xdfwriter</writer>
    <first_timestamp>5.1</first_timestamp>
    <last_timestamp>5.9</last_timestamp>
    <sample_count>9</sample_count>
    <clock_offsets>
        <offset>
            <time>50979.76</time>
            <value>-.01</value>
        </offset>
        <offset>
            <time>50979.86</time>
            <value>-.02</value>
        </offset>
    </clock_offsets>
</info>
```

#### Time-series data

| time_stamp |   0 |   1 |   2 |
|------------|-----|-----|-----|
|        5.1 | 192 | 255 | 238 |
|        5.2 |  12 |  22 |  32 |
|        5.3 |  13 |  23 |  33 |
|        5.4 |  14 |  24 |  34 |
|        5.5 |  15 |  25 |  35 |
|        5.6 |  12 |  22 |  32 |
|        5.7 |  13 |  23 |  33 |
|        5.8 |  14 |  24 |  34 |
|        5.9 |  15 |  25 |  35 |

These time-stamps precede the first clock offset measurement, but for
synchronization they will be handled with respect to the first (and
only in this case) detected clock segment.

#### Clock offsets

Clock offset times do not match the footer. This should not happen
with LabRecorder but as this file is code-generated it's just a
quirk. The footer values are not used for synchronization so they can
be safely ignored here.

|   time |   value |
|--------|---------|
|    6.1 |    -0.1 |
|    7.1 |    -0.1 |

### Stream 0x02C0FFEE / 46202862

1 string channel, 9 samples

#### Header

``` xml
<info>
    <name>SendDataString</name>
    <type>StringMarker</type>
    <channel_count>1</channel_count>
    <nominal_srate>10</nominal_srate>
    <channel_format>string</channel_format>
    <created_at>50942.723319709003</created_at>
    <desc/>
    <uid>xdfwriter_11_str</uid>
</info>
```

#### Footer

Identical to stream 0.

#### Time-series data

| time_stamp |            0 |
|------------|--------------|
|        5.1 | (XML footer) |
|        5.2 |        Hello |
|        5.3 |        World |
|        5.4 |         from |
|        5.5 |          LSL |
|        5.6 |        Hello |
|        5.7 |        World |
|        5.8 |         from |
|        5.9 |          LSL |

#### Clock offsets

No clock offsets, so synchronization will have no effect.


## clock\_resets.xdf
### Stream 1
#### Header

``` xml
<info>
	<name>MyMarkerStream</name>
	<type>Markers</type>
	<channel_count>1</channel_count>
	<nominal_srate>0</nominal_srate>
	<channel_format>string</channel_format>
	<source_id>myuidw43536</source_id>
	<version>1.1000000000000001</version>
	<created_at>564076.02850699995</created_at>
	<uid>1efcb4a6-8894-4014-b404-4b6f6b2205f2</uid>
	<session_id>default</session_id>
	<hostname>BP-LP-022</hostname>
	<v4address />
	<v4data_port>16572</v4data_port>
	<v4service_port>16572</v4service_port>
	<v6address />
	<v6data_port>16572</v6data_port>
	<v6service_port>16572</v6service_port>
	<desc />
</info>
```

#### Footer

``` xml
<info>
  <first_timestamp>653153.2121885</first_timestamp>
  <last_timestamp>259.6538279</last_timestamp>
  <sample_count>174</sample_count>
  <clock_offsets>
    <offset>
      <time>653156.02616855</time>
      <value>-652340.2838639501</value>
    </offset>
    <!-- cut -->
    <offset>
      <time>264.6430016000002</time>
      <value>1121.165595</value>
    </offset>
  </clock_offsets>
</info>
```

### Stream 2
#### Header

``` xml
<info>
	<name>BioSemi</name>
	<type>EEG</type>
	<channel_count>8</channel_count>
	<nominal_srate>100</nominal_srate>
	<channel_format>float32</channel_format>
	<source_id>myuid34234</source_id>
	<version>1.1000000000000001</version>
	<created_at>653103.26692229998</created_at>
	<uid>fa3e14ab-b621-480e-a9d5-c740f0e47140</uid>
	<session_id>default</session_id>
	<hostname>BP-LP-022</hostname>
	<v4address />
	<v4data_port>16573</v4data_port>
	<v4service_port>16573</v4service_port>
	<v6address />
	<v6data_port>16573</v6data_port>
	<v6service_port>16573</v6service_port>
	<desc />
</info>
```

#### Footer
``` xml
<info>
  <first_timestamp>653150.379117</first_timestamp>
  <last_timestamp>261.9267033</last_timestamp>
  <sample_count>27814</sample_count>
  <clock_offsets>
    <offset>
      <time>653156.0261441499</time>
      <value>-652340.28383985</value>
    </offset>
    <!-- cut -->
    <offset>
      <time>264.6385764000001</time>
      <value>1121.1656319</value>
    </offset>
  </clock_offsets>
</info>
```

## empty\_streams.xdf

Example containing empty and non-empty data and marker streams.

### Stream 1

1 `string` channel, 1 sample

#### Header

``` xml
<info>
	<name>ctrl</name>
	<type>control</type>
	<channel_count>1</channel_count>
	<channel_format>string</channel_format>
	<source_id>kassia</source_id>
	<nominal_srate>0.000000000000000</nominal_srate>
	<version>1.100000000000000</version>
	<created_at>91684.87631725401</created_at>
	<uid>4740b9ba-d45d-4e2b-9a4b-ee966d9b56df</uid>
	<session_id>default</session_id>
	<hostname>kassia</hostname>
	<v4address />
	<v4data_port>16572</v4data_port>
	<v4service_port>16572</v4service_port>
	<v6address />
	<v6data_port>0</v6data_port>
	<v6service_port>0</v6service_port>
	<desc>
		<manufacturer>pylsltools</manufacturer>
	</desc>
</info>
```

#### Footer

``` xml
<info>
  <first_timestamp>91725.014004246</first_timestamp>
  <last_timestamp>91725.014004246</last_timestamp>
  <sample_count>1</sample_count>
  <clock_offsets>
    <offset>
      <time>91716.691545932</time>
      <value>-1.889200211735442e-05</value>
    </offset>
    <!-- cut -->
    <offset>
      <time>91746.69261952251</time>
      <value>-3.837950498564169e-05</value>
    </offset>
  </clock_offsets>
</info>
```

#### Time-series data

|   time_stamp |            0 |
|--------------|--------------|
| 91725.014004 | {"state": 2} |

#### Clock offsets

|         time | value |
|--------------|-------|
| 91716.691546 |    ≅0 |
| 91721.691770 |    ≅0 |
| 91726.692053 |    ≅0 |
| 91731.692211 |    ≅0 |
| 91736.692330 |    ≅0 |
| 91741.692493 |    ≅0 |
| 91746.692620 |    ≅0 |

### Stream 2

Empty stream.

#### Header

``` xml
<info>
	<name>Empty marker stream: test stream 0 counter</name>
	<type>data</type>
	<channel_count>1</channel_count>
	<channel_format>string</channel_format>
	<source_id>test_stream.py:191748:0</source_id>
	<nominal_srate>0.000000000000000</nominal_srate>
	<version>1.100000000000000</version>
	<created_at>91696.18816467900</created_at>
	<uid>6f7e0288-10b8-4f48-89f8-0381ce20922f</uid>
	<session_id>default</session_id>
	<hostname>kassia</hostname>
	<v4address />
	<v4data_port>16574</v4data_port>
	<v4service_port>16574</v4service_port>
	<v6address />
	<v6data_port>0</v6data_port>
	<v6service_port>0</v6service_port>
	<desc>
		<manufacturer>pylsltools</manufacturer>
	</desc>
</info>
```

#### Footer

``` xml
<info>
  <first_timestamp>0</first_timestamp>
  <last_timestamp>0</last_timestamp>
  <sample_count>0</sample_count>
  <clock_offsets>
    <offset>
      <time>91716.691513728</time>
      <value>-2.540599962230772e-05</value>
    </offset>
    <!-- cut -->
    <offset>
      <time>91746.69276649199</time>
      <value>-2.026499714702368e-05</value>
    </offset>
  </clock_offsets>
</info>
```

#### Clock offsets

|         time | value |
|--------------|-------|
| 91716.691514 |    ≅0 |
| 91721.691774 |    ≅0 |
| 91726.692058 |    ≅0 |
| 91731.692287 |    ≅0 |
| 91736.692447 |    ≅0 |
| 91741.692554 |    ≅0 |
| 91746.692766 |    ≅0 |

### Stream 3

Empty stream.

#### Header

``` xml
<info>
	<name>Empty data stream: test stream 0 counter</name>
	<type>data</type>
	<channel_count>1</channel_count>
	<channel_format>float32</channel_format>
	<source_id>test_stream.py:191790:0</source_id>
	<nominal_srate>1.000000000000000</nominal_srate>
	<version>1.100000000000000</version>
	<created_at>91699.83395166400</created_at>
	<uid>ff430a18-9954-43f5-bb5f-f5589e3aa6a2</uid>
	<session_id>default</session_id>
	<hostname>kassia</hostname>
	<v4address />
	<v4data_port>16575</v4data_port>
	<v4service_port>16575</v4service_port>
	<v6address />
	<v6data_port>0</v6data_port>
	<v6service_port>0</v6service_port>
	<desc>
		<manufacturer>pylsltools</manufacturer>
		<channels>
			<channel>
				<label>ch:00</label>
				<type>misc</type>
			</channel>
		</channels>
	</desc>
</info>
```

#### Footer

``` xml
<info>
  <first_timestamp>0</first_timestamp>
  <last_timestamp>0</last_timestamp>
  <sample_count>0</sample_count>
  <clock_offsets>
    <offset>
      <time>91716.6915301265</time>
      <value>-2.211050014011562e-05</value>
    </offset>
    <!-- cut -->
    <offset>
      <time>91746.69269425601</time>
      <value>-1.128000440075994e-05</value>
    </offset>
  </clock_offsets>
</info>
```

#### Clock offsets

|         time | value |
|--------------|-------|
| 91716.691530 |    ≅0 |
| 91721.691776 |    ≅0 |
| 91726.692048 |    ≅0 |
| 91731.692247 |    ≅0 |
| 91736.692367 |    ≅0 |
| 91741.692487 |    ≅0 |
| 91746.692694 |    ≅0 |

### Stream 4

1 `int32` channel, 10 samples

#### Header

``` xml
<info>
	<name>Data stream: test stream 0 counter</name>
	<type>data</type>
	<channel_count>1</channel_count>
	<channel_format>int32</channel_format>
	<source_id>test_stream.py:191695:0</source_id>
	<nominal_srate>1.000000000000000</nominal_srate>
	<version>1.100000000000000</version>
	<created_at>91690.55328314200</created_at>
	<uid>bc60b7bb-e632-407c-b3db-e42f9cad4179</uid>
	<session_id>default</session_id>
	<hostname>kassia</hostname>
	<v4address />
	<v4data_port>16573</v4data_port>
	<v4service_port>16573</v4service_port>
	<v6address />
	<v6data_port>0</v6data_port>
	<v6service_port>0</v6service_port>
	<desc>
		<manufacturer>pylsltools</manufacturer>
		<channels>
			<channel>
				<label>ch:00</label>
				<type>misc</type>
			</channel>
		</channels>
	</desc>
</info>
```

#### Footer

``` xml
<info>
  <first_timestamp>91725.21394789348</first_timestamp>
  <last_timestamp>91735.21394789348</last_timestamp>
  <sample_count>10</sample_count>
  <clock_offsets>
    <offset>
      <time>91716.6915717245</time>
      <value>-1.94335007108748e-05</value>
    </offset>
    <!-- cut -->
    <offset>
      <time>91746.69274602149</time>
      <value>-3.694550105137751e-05</value>
    </offset>
  </clock_offsets>
</info>
```

#### Time-series data

|   time_stamp | ch:00 |
|--------------|-------|
| 91725.213948 |     0 |
| 91726.213948 |     1 |
| 91727.213948 |     2 |
| 91728.213948 |     3 |
| 91729.213948 |     4 |
| 91730.213948 |     5 |
| 91731.213948 |     6 |
| 91732.213948 |     7 |
| 91733.213948 |     8 |
| 91734.213948 |     9 |

#### Clock offsets

|         time | value |
|--------------|-------|
| 91716.691572 |    ≅0 |
| 91721.691773 |    ≅0 |
| 91726.692049 |    ≅0 |
| 91731.692249 |    ≅0 |
| 91736.692457 |    ≅0 |
| 91741.692557 |    ≅0 |
| 91746.692746 |    ≅0 |
